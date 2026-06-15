# Right-Sized Palantir-Foundry-Style Platform — Implementation Plan

Codename **Keystone** (placeholder; rename freely). Single-developer, air-gapped Windows dev box now → Kubernetes later.

> This is the synthesized, chosen plan — the "best of both" of `palantir-inspired-data-platform-a.md` and `palantir-inspired-data-platform-b.md`, right-sized for an air-gapped single dev machine.

---

## Context

`pal-docs/` currently holds only a scraped archive of Palantir's public docs (`palantir-docs/`, ~5k markdown files) and two architecture drafts (`architecture/palantir-inspired-data-platform-a.md`, 2,476 lines; `…-b.md`, 1,070 lines). There is **no implementation yet** — this is greenfield.

Both drafts describe the same Foundry-like product (Data Connection → Datasets → Pipelines → Ontology → Data Health, plus Actions/Functions) but specify a **40-service distributed stack** (Kubernetes, Spark, Flink, Kafka/Redpanda, Trino, Iceberg + Nessie catalog, OpenSearch, Qdrant, Neo4j/JanusGraph, ClickHouse, Keycloak, Vault, OPA + SpiceDB/OpenFGA, Prometheus/Loki/Tempo/Grafana, …). That is correct for a Palantir-scale SaaS and **wrong for a single air-gapped dev machine**.

**Goal:** take the *concepts* both drafts get right (everything-is-a-resource, transactional datasets, immutable raw + derived serving layers, the Ontology as a live permissioned semantic API, content-validity vs operational-health as separate planes) and implement them on the **smallest stack that delivers real capability** — using third-party software only where building it ourselves would waste serious effort (a database, a query engine, a versioned table format), and replacing every heavyweight distributed component with an embedded or in-process equivalent **behind a plugin seam** so the heavy version can return for production.

**Intended outcome:** a runnable, plugin-based platform where *each subsystem is owned by a swappable plugin behind a stable contract*; security/auth is real but self-contained locally (local users now, Okta/OIDC later); and the whole thing is one Python codebase running as two processes against one Postgres + the local filesystem — yet containerizes cleanly to Kubernetes when it leaves the dev box.

### Decisions locked from clarifying questions
- **Backend:** Python + FastAPI.
- **Dev target:** air-gapped **Windows, x86_64** on-prem dev box. **Prod target later:** Kubernetes (Linux). Design must containerize to two Deployments with no rewrite.
- **Dev mode:** develop *fully offline*. You can vendor **npm packages and Python packages** (local cache/wheelhouse) and **copy binary zips/executables** to the box.
- **Stage now (even if built later):** Documents & OCR, Streaming & CDC, S3 + containers, LLM & embeddings, **and trainable ML models (Palantir/Dataiku-style)**. Air-gapped means *download once, now* — see the offline bundle (§11).

---

## 1. Guiding decisions (synthesis verdict)

| Decision | Choice | Replaces (from drafts A/B) | Why it's right-sized |
|---|---|---|---|
| Topology | **Modular monolith + 1 worker process** | 5 planes as separate services; K8s | Two Python processes on one box; same modules become two K8s Deployments later. |
| Language | **Python 3.12 + FastAPI** | Go/Kotlin microservices | Native to the embedded data stack & plugin discovery; easiest Windows-offline vendoring. |
| System-of-record DB | **PostgreSQL 16 + pgvector** | metadata DB + ClickHouse + OpenSearch + Qdrant/Milvus + Neo4j/JanusGraph | One engine: metadata, object serving, full-text (`tsvector`), vectors (`pgvector`), graph (recursive CTE). |
| Analytical compute | **DuckDB (embedded) + Polars/PyArrow** | Spark + Trino | In-process OLAP over Parquet/Delta/CSV/JSON; SQL pushdown for pipeline nodes. |
| Versioned datasets | **delta-rs (`deltalake`)** + a trivial `parquet_snapshot` backend | Iceberg + Nessie/REST catalog + Spark | ACID, time-travel, MERGE, schema evolution — **no JVM, no catalog, no Spark**. Don't hand-roll a transaction log. |
| Object storage | **Local filesystem** behind `StorageBackend` | Ceph RGW | Zero service. MinIO staged as a drop-in for S3-API parity (prod). |
| Job queue / orchestration | **Postgres `SELECT … FOR UPDATE SKIP LOCKED` + in-repo worker** | Temporal / Celery+Redis / Kafka-as-bus | Durable, no broker. The worker is the *same package* launched twice. |
| Internal event bus | **In-process bus + durable `events` table** | Kafka/Redpanda (internal) | Synchronous + replayable on one node. (Kafka *as a data source* is just a connector, later.) |
| AuthN | **Local provider** behind `AuthProvider` | Keycloak | Local users now; `oidc`/`okta` plugin drops in later with zero downstream change. |
| AuthZ | **In-process `Authorizer`** (roles + markings + object/property policy) | OPA + SpiceDB/OpenFGA services | Real policy *model*; engine is a function call + SQL predicate. Seam to externalize. |
| Secrets | **`local_encrypted`** (libsodium sealed box in PG) behind `SecretStore` | Vault | Master key from env/OS; never logged. `vault` plugin later. |
| Observability | **structlog + `runs`/`run_events`/`metrics` tables surfaced in the UI** | Prometheus + Loki + Tempo + Grafana | App-native Health/Lineage views; OTel-shaped seam only. |
| Plugin mechanism | **`pluggy` (hooks) + entry-points (discovery) + Pydantic v2 (manifest/config validation)** | custom registry | Battle-tested (pytest/Datasette); zero infra; the centerpiece of "each part owned by something". |
| Frontend | **React + Vite + Blueprint.js + React Flow + Monaco + TanStack Query/Table** | — | Blueprint is Palantir's own OSS design system → the right dense, dark, resource-oriented look. Built to static assets served by FastAPI. |

**Net effect:** the ~40-service stack collapses to **two processes, one database, one embedded engine, and the filesystem** — everything else is a *library*, not a service. Every deleted heavyweight has a named seam (a plugin type or swappable facade) so Okta, Vault, OpenFGA, OpenSearch, Qdrant, Iceberg, MinIO, Kafka/Flink, and Prometheus can return for Kubernetes **without touching the kernel or services** — only by adding a plugin and flipping an id in config.

---

## 2. Architecture: modular monolith + worker

Single repo, `src/` layout, two installable packages: **`keystone_contracts`** (Protocols + Pydantic models + `pluggy` hookspecs — *zero* dependency on the kernel) and **`keystone`** (kernel + services + built-in plugins + API). Two runtime processes:

- **API process** — FastAPI; thin routers → services; serves the built React assets.
- **Worker process** — same package; runs `runs.worker_loop()` pulling jobs from Postgres (`SKIP LOCKED`). All sync/transform/materialization/training runs here, never on the request path.

**Dependency rule (enforce with `import-linter`):** `api → services → kernel → keystone_contracts`. Plugins import **only** `keystone_contracts`. Services never import `plugins_builtin`. This is what makes everything swappable and testable, and what lets the same code containerize into separate API/worker images for K8s.

```
src/
  keystone_contracts/      # Protocols, Pydantic manifests/models, pluggy hookspecs   (the stable spine)
  keystone/
    kernel/                # small, boring, stable — owns the spine, not capabilities
      resources/           # resources supertype, opaque IDs, markings, ownership ("everything is a resource")
      plugins/             # entry-point discovery, manifest validation, pluggy mgr, capability index, kill-switch
      runs/                # job queue (SKIP LOCKED), run ledger/state machine, worker loop
      security/            # AuthProvider facade, in-proc Authorizer, SecretStore facade, audit writer
      lineage/             # append-only lineage_edges + traversal queries
      events/              # in-proc bus + durable events table
      config/              # settings, DI container, WorkerContext factory
    services/              # domain logic; orchestrates plugins; NO plugin imports
      data_connection/  datasets/  pipelines/  validity/  health/
      ontology/  actions/  functions/  models/  query/   # query/ = DuckDB session mgr
    plugins_builtin/       # day-one plugins, each registered as a `keystone.plugins` entry point
      connectors/{postgres,rest,file,upload}/
      storage/fs/   dataset/{delta,parquet_snapshot}/
      auth/local/  secrets/local_encrypted/
      nodes/{select,filter,join,union,aggregate,cast,parse_json,dedupe,python,model_predict}/
      checks/{not_null,unique_pk,enum,regex,row_count,referential}/
      indexes/{relational,search,vector,graph}/
      effects/{ontology_edit,webhook}/   runtimes/{python_inproc,python_subprocess}/
      modelruntimes/{sklearn,xgboost}/   schedulers/{manual,cron,on_input_update}/
    api/                   # FastAPI routers (thin) + static asset serving
    worker/                # worker entrypoint
ui/                        # React + Vite + Blueprint; build → keystone/api/static/
```

**Inter-module interfaces (narrow facades):** `kernel.security.authorize(principal, op, resource)`, `kernel.runs.enqueue(job)`, `kernel.lineage.record(edge)`, `kernel.plugins.get(capability, id) -> hookimpl`. Plugins are always invoked with an injected `WorkerContext` (their only door to the outside: `storage`, `dataset_backend`, `secrets.resolve(handle)`, `emit_metric`, `emit_lineage`, `log`) — this is where secret-resolution scoping and log redaction are enforced.

---

## 3. The plugin spine (the centerpiece — "each part owned by something")

### 3.1 Kernel owns the spine, never the capabilities
1. **Resource graph & identity** — `resources` supertype, opaque prefixed IDs (`ds_`, `ot_`, `src_`, `mdl_`…), project→folder→resource parentage, ownership, markings, soft-delete.
2. **Plugin host** — entry-point discovery, Pydantic manifest validation, `pluggy` PluginManager, capability index, `api_version` compat gate, **quarantine** (a bad plugin is recorded with status+error, never crashes the kernel) and **kill-switch**.
3. **Run ledger & queue** — `runs`, `run_events`, `SKIP LOCKED` job table, state machine.
4. **Security facade** — AuthProvider + Authorizer + audit; every mutating request/action passes through.
5. **Lineage recorder** — append-only `lineage_edges`, one emit API.
6. **Event bus** — in-proc synchronous dispatch + durable `events` table.
7. **Config & secrets facade**.

### 3.2 Extension points (the full ownership map — 13 plugin types)
| # | Plugin type | Owns | Day-one → later |
|---|---|---|---|
| 1 | **AuthProvider** | authenticate principal, resolve groups | `local` → `oidc`/`okta` |
| 2 | **SecretStore** | store/resolve secrets | `local_encrypted` → `vault` |
| 3 | **Connector** | talk to a source; declares capabilities | `postgres`,`rest`,`file`,`upload` → `salesforce`,`kafka`,CDC |
| 4 | **StorageBackend** | bytes at rest (`put/get/list/presign`) | `fs` → `s3`/`minio` |
| 5 | **DatasetBackend** | versioned table storage | `delta`,`parquet_snapshot` → `iceberg` |
| 6 | **TransformNode** | one pipeline node (infer-schema + execute) | `select…python`,`model_predict` → `llm`,`ocr`,`embed` |
| 7 | **FunctionRuntime** | execute user logic (sandbox + I/O contract) | `python_inproc`,`python_subprocess` → `container` |
| 8 | **ValidityCheck** | one content-validity check | `not_null`,`unique_pk`,`enum`,`regex`,`row_count`,`referential` |
| 9 | **ObjectIndex** | serve objects for one capability | `relational`,`search`,`graph` → `vector` |
| 10 | **ActionHandler/Effect** | one action side-effect | `ontology_edit`,`webhook` → `external_writeback`,`notify` |
| 11 | **Scheduler/Trigger** | when a job runs | `manual`,`cron`,`on_input_update` → `event_driven` |
| 12 | **ModelRuntime** | train / evaluate / score ML models | `sklearn`,`xgboost` → `lightgbm`,`pytorch` |
| 13 | **ModelProvider (LLM)** | text gen / embeddings | (later) `ollama`,`local_embeddings` |

(*DuckDB is wired directly behind a thin internal seam, **not** a plugin type yet — promote only if a second engine ever appears. Deliberate "don't over-abstract" call.*)

### 3.3 Contract shape (every plugin = manifest + config model + hookimpls)
```python
class ConnectorManifest(BaseModel):
    id: str; display_name: str; family: str
    capabilities: list[Capability]          # explore|batch_sync|incremental_sync|cdc_sync|media_sync|file_export|webhook|virtual_table|use_in_code
    config_schema: type[BaseModel]          # validates Source config
    supported_auth: list[str]; api_version: str = "1.0"

class Connector(Protocol):
    manifest: ClassVar[ConnectorManifest]
    def test(self, cfg, secret: SecretHandle) -> TestResult: ...
    def explore(self, cfg, secret, locator: str | None) -> ExploreResult: ...
    def sync(self, req: SyncRequest, ctx: WorkerContext) -> SyncResult: ...   # SyncResult: rows_read, new_cursor, arrow_batches_ref

class DatasetBackend(Protocol):
    def begin(self, dataset_id, txn_type) -> Txn          # SNAPSHOT|APPEND|UPDATE|DELETE|MERGE
    def write(self, txn, batches: pa.RecordBatchReader); def commit(self, txn) -> CommitInfo; def abort(self, txn)
    def scan(self, dataset_id, version=None) -> pa.RecordBatchReader; def schema(...); def history(...) -> list[CommitInfo]

class TransformNode(Protocol):
    def infer_schema(self, in_schemas, params) -> Schema   # for live preview
    def to_sql(self, ctx) -> str | None                    # DuckDB pushdown when possible
    def execute(self, ctx) -> pa.RecordBatchReader         # fallback / non-SQL nodes

class ObjectIndex(Protocol):
    def upsert(self, object_type_id, batches, version); def delete(self, object_type_id, keys)
    def query(self, q: ObjectQuery, principal: Principal) -> ObjectPage   # MUST inject authz predicate

class ModelRuntime(Protocol):
    def train(self, spec: TrainSpec, ctx) -> ModelArtifactRef            # reads a dataset, writes a versioned artifact
    def evaluate(self, model_ref, dataset, ctx) -> Metrics
    def predict(self, model_ref, batches, ctx) -> pa.RecordBatchReader   # batch scoring (also exposed as model_predict node + function)
```

### 3.4 Discovery / loading / selection
- **Discovery:** built-in *and* third-party plugins register through the **same** entry-point group `keystone.plugins` — no privileged built-ins, one code path.
- **Load:** import → validate manifest (Pydantic) → check `api_version` → register hookimpls with `pluggy`; failures → quarantine row in `plugins` table.
- **Selection:** resources name their plugin by id (`source.connector_id`, `dataset.backend_id`, `object_type.index_ids`, `model.runtime_id`). Swapping an implementation = changing an id, not code. The "Plugins" admin view lists what's installed and who owns what.

### 3.5 "Everything is a resource"
One `resources` table is the supertype; per-type tables join by `resource_id`. AuthZ, lineage, audit, search, and the UI tree all operate on this one table — so a new resource type (a new plugin's output) inherits permissions, lineage, search, and health **for free**.

---

## 4. Data & storage model
- **Lakehouse = system of record for dataset *content*** — Parquet/Delta files on the local filesystem (via `StorageBackend`/`DatasetBackend`). **Raw landing is immutable**; curated layers are derived & rebuildable (draft B's North Star).
- **Postgres = system of record for *metadata*** — resource graph, transaction summaries (current version/schema/row-count/markings as a *pointer* to the authoritative `_delta_log`), ontology serving tables, search/vector/graph indexes, runs, lineage, audit. **Never** the primary copy of big dataset rows.
- Two `DatasetBackend`s day one: `delta` (default, versioned, MERGE/time-travel) and `parquet_snapshot` (dead-simple, for uploads/previews). `iceberg` later.

---

## 5. Ontology model on Postgres (the differentiator)

**Type-level (definitions, small, versioned):** `ontology_versions`, `object_types` (api_name, primary_key_property, backing_dataset_id+version, materialization_mode, title_property), `object_properties` (data_type, source_column, value_type_id, is_indexed_search/vector, marking_id, visibility_policy_id), `shared_properties`, `value_types` (regex/enum/range constraints), `interfaces` (polymorphism), `link_types` (from/to object type, cardinality, derived-FK vs mapped-link-dataset), `action_types`, `function_defs`, `models`/`model_versions`.

**Instance-level (serving, materialized from curated datasets):** for each object type a physical table `obj_<api_name>(pk PK, properties jsonb, <promoted indexed cols>, search_tsv tsvector GENERATED, embedding vector(N) NULL, _src_dataset_version, _row_refs jsonb, _markings int[])` with `GIN(search_tsv)`, `HNSW(embedding)`, btree on promoted cols, `GIN(_markings)`. Links → `link_<name>(from_pk, to_pk, _markings int[], PK(from_pk,to_pk))` (derived links may be a VIEW; mapped links a real table).

**One Ontology API, four `ObjectIndex` plugins over the same `obj_*` tables:** `relational` (filter/sort/paginate point-lookups), `search` (`search_tsv @@ websearch_to_tsquery`), `vector` (`ORDER BY embedding <=> $q`), `graph` (recursive CTE neighborhood/path). **Security is in the query path:** every `query()` appends `AND has_access(_markings, principal) AND <object-policy predicate>` and projects out columns the principal can't see (property-level markings) — Foundry's mandatory+discretionary+granular model as SQL, no OPA call.

**Materialization flow (on the worker):** curated Delta dataset → DuckDB read → map columns→properties (+ ontology validity: PK unique/non-null, links resolve) → `ObjectIndex.relational.upsert` → generated `search_tsv` → (later) embeddings → emit `dataset→object_type` lineage → record run. Modes: snapshot rebuild / incremental append / merge-by-PK. *Process/log objects* and *Document/DocumentChunk* are ordinary object types — no special-casing.

---

## 6. Security / auth model (real, in-process, with prod seams)
- **AuthProvider** (`Principal{id,username,groups,is_service,attributes}`): `local` impl now — `users`/`groups`/`user_groups`/`service_accounts`, Argon2id hashes, signed-token or DB sessions, seeded admin on first run. **`oidc`/`okta` seam later** implements the same Protocol (auth-code redemption, JWKS verification, claims→groups). Kernel & services only ever see `Principal` — nothing downstream knows whether auth was local or Okta. Switching = changing the active provider id in config. *This is exactly the "auth is there but not plugged into anything" requirement.*
- **Authorizer** (in-process): `authorize(principal, op, resource)`, `visible_markings`, `object_predicate`, `visible_properties`. Tables: `roles`/`role_grants` (discretionary, project/folder/resource scope), `markings`/`principal_markings`/`resource_markings` (mandatory, set-containment, **union-propagated through lineage**), `object_policies` (row predicate), `property_policies` (column projection). Seam: a `RemoteAuthorizer` can later back the same methods with OpenFGA/OPA — the *model* is designed now so migration is data-only.
- **SecretStore** (`local_encrypted`): libsodium sealed boxes in a `secrets` table; master key from env var/OS keyring; resolved only inside a scoped `WorkerContext`; structured-log redaction filter. `vault` plugin later.
- **Audit** (`audit_events`, append-only): actor, op, resource, before/after, reason, markings, request_id — written by the security facade on every mutation/action; shown in each resource's Audit tab.

---

## 7. ML & AI (Palantir/Dataiku-style, all staged now, built in later phases)
- **Model** is a first-class resource; **ModelRuntime** plugins (`sklearn`, `xgboost`/`lightgbm`, optional `pytorch` CPU) own train/evaluate/predict. Training runs as a worker job; artifacts are versioned via `StorageBackend` and registered in `models`/`model_versions` (metrics, lineage to training dataset).
- Scoring is exposed **two ways** (mirrors Foundry & Dataiku): a `model_predict` **TransformNode** (batch scoring in pipelines) and a **Function** (online scoring for actions/object views).
- **Notebooks** (JupyterLab, staged) give the code-first modeling surface (Foundry Code Workspaces / Dataiku notebooks analog). Visual/AutoML point-and-click is a later guided config over the same ModelRuntime.
- **LLM/AIP-assist & embeddings:** `ModelProvider` seam → `ollama` (local LLM) powers an `llm` TransformNode (classify/extract/summarize) and an assist helper; a local `sentence-transformers`/ONNX embedding model powers the `embed` node → pgvector → semantic search. Optional, CPU-only, offline (`HF_HUB_OFFLINE=1`).

---

## 8. Phased roadmap (each phase ships something runnable; exit criteria are demoable)

- **Phase 0 — Kernel & plugin spine.** `keystone_contracts`; plugin host (discover/validate/quarantine/kill-switch); `resources`+IDs+markings; run ledger + `SKIP LOCKED` queue + worker process; in-proc event bus; security facade + audit; FastAPI shell + React app frame + login + Plugins admin view. Plugins: `auth/local`, `secrets/local_encrypted`. **Exit:** log in as local user; create project/folder; see audit; a no-op plugin loads via entry points and appears in the admin view; worker drains a trivial job.
- **Phase 1 — Data Connection + Datasets.** Sources/syncs + capability dispatch; dataset lifecycle/transactions; DuckDB preview; source→dataset lineage. Plugins: connectors `postgres`/`rest`/`file`/`upload`; storage `fs`; dataset `delta`+`parquet_snapshot`; scheduler `manual`+`cron`. **Exit:** batch-sync a Postgres table into a Delta dataset; drag-drop a CSV; preview rows; failed sync commits nothing; transaction history + lineage visible.
- **Phase 2 — Pipelines + Validity + Health.** Pipeline graph + compile + per-node schema inference (live preview) + execution (DuckDB pushdown, Polars/Python fallback); validity contracts + enforcement; health monitors (status/freshness/row-count) + issue lifecycle; lineage through transforms. Plugins: nodes `select…dedupe`+`python`; checks `not_null…referential`. **Exit:** build raw→curated pipeline, preview each node; a PK/row-count check blocks publish; Content-Validity vs Operational-Health tabs both populated; lineage spans source→raw→pipeline→curated.
- **Phase 3 — Ontology.** Object/link/value/shared types + interfaces; materializer; object API (filter/search/graph). Plugins: indexes `relational`/`search`/`graph` (vector stub). **Exit:** map curated dataset → `Customer` with PK; define `Customer→Order` link; object query returns only authorized objects (markings + object policy enforced in SQL); graph traversal in UI; ontology lineage visible.
- **Phase 4 — Actions & Functions.** Action types (parameters, submission criteria, before/after audit); function registry; ontology writeback. Plugins: effects `ontology_edit`/`webhook`; runtimes `python_inproc`+`python_subprocess`. **Exit:** define a permissioned, audited action that edits an object; a function-backed action; a webhook effect with an idempotency key.
- **Phase 5 — Media, Search & Embeddings.** Media sets; document pipeline (Tika→OCR→chunk→embed); activate `vector` index (pgvector HNSW); Document/DocumentChunk object types; semantic search. Plugins: nodes `ocr`/`chunk`/`embed`. **Exit:** upload PDFs → searchable chunks → Document objects → semantic search returns chunks.
- **Phase 6 — Models & ML (+ optional LLM/AIP-assist).** Model resource + registry; `sklearn`/`xgboost` ModelRuntime; training jobs; `model_predict` node + scoring function; JupyterLab notebooks; optional `ollama` LLM node + assist. **Exit:** train a model on a dataset, register a version with metrics, score in a pipeline and online via a function; (optional) an `llm` node classifies rows.
- **Phase 7 — Streaming/CDC + externalize for Kubernetes.** Kafka connector + micro-batch CDC + stream freshness/lag; then flip prod seams: `s3`/`minio` storage, `oidc`/`okta` auth, `vault` secrets, external policy engine, containerized API+worker on K8s. **Exit:** a topic micro-batches into a dataset with lag in Health; the same images run on a K8s namespace with S3 + Okta.

*Deferred until prod scale demands it: Spark/Flink, Iceberg+catalog, Trino, OpenSearch/Qdrant/Neo4j, Prometheus/Loki/Tempo. Each already has a seam.*

---

## 9. Dev → Kubernetes continuity
The dev choices map 1:1 to prod with no rewrite: modular monolith → **two images** (api, worker) → two Deployments; `fs`→`s3`/`minio`; `local` auth→`okta` OIDC; in-proc Authorizer→OpenFGA/OPA; `local_encrypted`→`vault`; Postgres stays (managed/StatefulSet); app-native health → optionally export OTel to Prometheus/Loki/Tempo. Keep the app 12-factor (config via env, no local state beyond the DB + object store) from Phase 0 so containerizing is trivial.

---

## 10. Critical files to create (greenfield, in build order)
- `src/keystone_contracts/__init__.py` — all plugin Protocols, Pydantic manifests/config models, `pluggy` hookspecs (**the spine — build first**).
- `src/keystone/kernel/plugins/host.py` — entry-point discovery, manifest validation, `pluggy` manager, capability index, quarantine/kill-switch.
- `src/keystone/kernel/resources/graph.py` — `resources` supertype, opaque IDs, markings, ownership.
- `src/keystone/kernel/runs/worker.py` — `SKIP LOCKED` queue, run ledger/state machine, worker loop.
- `src/keystone/kernel/security/{authorizer.py,providers.py,audit.py}` — Authorizer + AuthProvider/SecretStore facades + audit.
- `src/keystone/plugins_builtin/dataset/delta/backend.py` — first real `DatasetBackend`.
- `src/keystone/services/ontology/materializer.py` — Phase-3 centerpiece.
- `pyproject.toml` — declares built-ins as `keystone.plugins` entry points + wheelhouse-pinned deps; `requirements.lock`.
- `ui/` — Vite + Blueprint app; build → `src/keystone/api/static/`.
- `import-linter` contract enforcing `api → services → kernel → keystone_contracts`; plugins → contracts only.

---

## 11. Offline pre-stage bundle — **Windows x86_64** (download now; you can't fetch later)

You can vendor **Python packages** (build a wheelhouse) and **npm packages** (npm cache / vendored `node_modules`) and **copy binary zips/executables**. Build the Python wheelhouse and npm cache on an **online Windows x86_64** machine (or with `--platform win_amd64 --only-binary=:all:`) so binaries match. Pin everything (`requirements.lock`, `package-lock.json`). Capture this list as `OFFLINE_BUNDLE.md` in the repo.

**A. Python (core).** CPython 3.12 Windows x64 installer. **Wheelhouse** (`pip download` → `pip install --no-index --find-links wheelhouse`), including: `fastapi`,`uvicorn[standard]`,`pydantic`,`pydantic-settings`,`python-multipart`,`httpx`; `pluggy`,`typing-extensions`; `psycopg[binary]`,`sqlalchemy`,`alembic`,`pgvector`; `duckdb`,`polars`,`pyarrow`,`deltalake`,`pyiceberg`(future),`pandas`; `argon2-cffi`,`pynacl`,`pyjwt[crypto]`,`cryptography`,`authlib`(future OIDC); `structlog`,`orjson`,`tenacity`,`python-dateutil`; dev: `pytest`,`pytest-asyncio`,`ruff`,`mypy`,`import-linter`,`hatchling`,`pip-tools`. *All ship `win_amd64` wheels.*

**B. PostgreSQL 16 + pgvector — the single fiddliest Windows item.** Recommended low-friction path: **conda-forge** (`postgresql` + `pgvector` both have `win-64` builds) vendored as an offline channel, OR the EDB Postgres **portable zip** + a **pre-built `pgvector`** (build `vector.dll`/`.control`/SQL on an online Windows box with **MSVC Build Tools** against the same PG 16, then copy into `lib`/`share/extension`). Ensure `contrib` (for `pg_trgm`) is included. *pgvector is only needed from Phase 5, but stage it now.*

**C. Node + frontend.** Node 20 LTS Windows x64 zip. Vendor the npm deps (`react`,`react-dom`,`vite`,`@blueprintjs/{core,icons,table}`,`reactflow`,`@monaco-editor/react`+`monaco-editor`,`@tanstack/{react-query,react-table}`,`typescript`) as an **npm cache** (`npm ci --offline --cache ./npm-cache`) and/or vendored `node_modules`; commit `package-lock.json`. *Monaco caveat:* ensure Vite bundles its web-workers locally (no CDN); Blueprint icons/fonts are local.

**D. DuckDB extensions.** The `duckdb` wheel is self-contained, but extensions (`delta`,`json`,`fts`,`vss`,`httpfs`,`excel`) **auto-download over HTTPS** — pre-download the `windows_amd64` `.duckdb_extension` files **matching the exact DuckDB version**, place in a local dir, `SET extension_directory=…` and `LOAD` from path.

**E. Java (for Tika & Kafka).** Temurin/Adoptium **JRE 17 or 21 Windows x64 zip**.

**F. Documents & OCR.** Apache **Tika** server jar (or tika-app jar); **Tesseract** Windows build (UB Mannheim) + `tessdata` language packs; `pytesseract` wheel; optionally `unstructured` wheels (heavy deps — stage carefully).

**G. LLM & embeddings.** **Ollama** Windows installer + **pre-pulled model blobs** (copy `%USERPROFILE%\.ollama\models`), or `llama.cpp` Windows binary + a GGUF file. Embeddings: a **sentence-transformers/ONNX model directory** copied over (set `HF_HUB_OFFLINE=1`,`TRANSFORMERS_OFFLINE=1`) + `sentence-transformers`/`transformers`/`onnxruntime` and **`torch` (CPU) win_amd64** wheels.

**H. ML training.** `scikit-learn`,`xgboost`,`lightgbm`,`numpy`,`scipy`,`statsmodels` wheels (all `win_amd64`); `torch` CPU (from G) for deep models; **JupyterLab** wheels + its npm/labextension assets for notebooks.

**I. Streaming & CDC.** Kafka client wheels (`confluent-kafka` or `aiokafka`). For a local broker on Windows: **Kafka** tarball (runs on the Temurin JRE via `.bat`); **Redpanda has no native Windows server** (would need Docker/WSL). Basic DB CDC via the worker needs no broker.

**J. S3 & containers.** **MinIO** `minio.exe` + `mc.exe`. **Docker on Windows caveat:** Docker Desktop needs WSL2/Hyper-V (WSL2 kernel update `wsl_update_x64.msi` must be staged) — may be unavailable on a locked-down server. **Default the `FunctionRuntime` to `python_subprocess` isolation, not containers**; only stage `docker save` image tarballs if Docker is actually present.

**K. Build tools (fallback).** **Visual Studio Build Tools (MSVC, win_amd64)** offline layout — for building pgvector and any package without a wheel.

---

## 12. Top risks / over-engineering traps to avoid
1. **Building the plugin framework before any plugin does real work** — build the *narrowest* contract Phase-1 needs; the 13 types are the target, not Phase-0 scope.
2. **Over-abstracting the query engine** — wire DuckDB directly; promote to a plugin only if a 2nd engine appears.
3. **Hand-rolling the dataset transaction log** — use delta-rs; atomic commit/time-travel is genuinely hard.
4. **Background work in the web process** — keep it on the worker + `SKIP LOCKED` queue.
5. **Postgres as the dataset content store** — content stays in the lakehouse; PG holds metadata + *materialized* serving projections only.
6. **Microservice envy** — modular monolith now; the plane *concepts* survive as modules, the *process boundaries* don't (until K8s).
7. **Streaming/CDC & external policy engines too early** — defer to Phase 7; micro-batch + in-proc authz first.
8. **Frontend scope explosion** — one generic resource-detail layout (Overview/Schema/Runs/Lineage/Health/Permissions/Audit tabs) reused across all resource types; build one workflow per phase.
9. **Air-gap runtime surprises (Windows-specific)** — DuckDB extensions, HuggingFace model downloads, Monaco web-workers, pgvector build, Docker/WSL2 — all silently need the internet or MSVC. Verify each works locally *before* disconnecting; bake `*_OFFLINE=1` env vars and local extension/model dirs into config.

---

## 13. Verification (per phase, end-to-end)
- **Plumbing:** `pytest` unit/integration suites per module; `import-linter` enforces the dependency rule; a smoke test asserts the plugin host discovers built-ins via entry points and quarantines a deliberately-broken plugin.
- **Run the app:** start Postgres, launch API + worker, `npm run build` the UI; log in as the seeded local admin.
- **Phase 1:** sync a local Postgres table and drag-drop a CSV → preview rows in the UI; kill a sync mid-run → assert no partial transaction committed; open the dataset's Lineage + Transactions tabs.
- **Phase 2:** build a raw→curated pipeline in the UI, preview each node; add a `unique_pk` check that fails → assert publish is blocked and a Content-Validity issue appears (distinct from Operational-Health).
- **Phase 3:** map a dataset → `Customer` object type, define a link, run the materializer; query objects as a restricted user → assert markings/object-policy filter rows and property-policy nulls columns *in SQL*; traverse the graph in the UI.
- **Phase 4:** execute a permissioned action → assert before/after in `audit_events`; trigger a webhook effect twice with the same idempotency key → assert one effect.
- **Phases 5–7:** PDF → OCR → chunk → embed → semantic search returns chunks; train + register + score a model (batch node + online function); micro-batch a Kafka topic with visible lag; finally build the api/worker images and run them on a K8s namespace with `s3` + `okta` to confirm the seams hold.

---

## 14. What this deliberately is NOT (kept simple on purpose)
One DB, one embedded engine, two processes, filesystem storage, in-proc bus/auth/authz/secrets, micro-batch instead of streaming, materialized PG tables instead of a search/vector/graph zoo, a modular monolith instead of services. Every one of these has a named seam so the production (Kubernetes) versions — Okta, Vault, OpenFGA/OPA, OpenSearch, Qdrant, Iceberg, MinIO, Kafka/Flink, Prometheus — can return **without touching the kernel or services**, only by adding a plugin and flipping an id in config. That is the whole point: smart and extensive at the seams, minimal in the running footprint.
