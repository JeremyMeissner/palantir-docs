# Keystone — Exhaustive Build Steps (LLM Execution Manual)

This is the **complete, ordered, checkbox-driven** execution guide for building the platform described in `architecture/keystone-implementation-plan.md`. It assumes **all tools/software are already downloaded and present on the air-gapped Windows x86_64 dev box** (per the plan §11 offline bundle).

> **How an executing LLM must use this document**
> - Work **top to bottom**. Do not start a step until its prerequisites are checked.
> - Each step has a stable ID (e.g. `P0-07`). When you complete a step, change `- [ ]` to `- [x]`.
> - **Never skip the per-phase Gate (`*-GATE`) or Exit (`*-EXIT`) steps.** A phase is not done until every box under it is `[x]`.
> - Apply the **Global Conventions (§0)** to *every* file you write. They are rules, not optional.
> - After each code change, keep the **green-gate** invariant: `ruff` + `mypy` + `import-linter` + `pytest` all pass.
> - If a step is ambiguous, re-read the referenced section of `keystone-implementation-plan.md` (cited inline as *Plan §N*). Do not invent infrastructure the plan deletes.
> - Commit after each completed step group with a message referencing the step IDs.

**Legend:** 🟦 code · 🟥 DB migration · 🟩 plugin · 🟨 API · 🟪 UI · 🧪 tests · ✅ verification

---

## 0. Global Conventions & Guardrails (apply to EVERY step)

- [ ] **CONV-01** Language/runtime: **Python 3.12**, `src/` layout, two installable packages: `keystone_contracts` and `keystone`. (*Plan §2*)
- [ ] **CONV-02** Dependency rule, enforced by `import-linter`: `api → services → kernel → keystone_contracts`. **Plugins import ONLY `keystone_contracts`.** `services` must never import `keystone.plugins_builtin`. (*Plan §2*)
- [ ] **CONV-03** Every plugin = **manifest (Pydantic) + config model (Pydantic) + hookimpls (pluggy)**, registered via the `keystone.plugins` entry-point group in `pyproject.toml`. Built-ins and third-party plugins use the **same** discovery path. (*Plan §3.3–3.4*)
- [ ] **CONV-04** Plugins touch the outside world **only** through an injected `WorkerContext` (`storage`, `dataset_backend`, `secrets.resolve(handle)`, `emit_metric`, `emit_lineage`, `log`). Never let a plugin import kernel internals or read raw secrets directly. (*Plan §2, §3.3*)
- [ ] **CONV-05** IDs are opaque, prefixed, sortable: implement `new_id(prefix: str) -> str` (prefix + ULID/base32). Prefixes: `proj_ fol_ src_ sync_ ds_ pl_ ot_ lt_ at_ fn_ mdl_ run_ job_ ev_ usr_ grp_ sa_ sec_ mk_ pol_ med_ str_`. (*Plan §3.1*)
- [ ] **CONV-06** All timestamps are UTC `timestamptz`. All money/decimals use exact types. No naive datetimes.
- [ ] **CONV-07** **Every schema change is an Alembic migration.** Never mutate tables by hand. Migrations are forward-only + tested by `upgrade`/`downgrade`.
- [ ] **CONV-08** DB access via **SQLAlchemy 2.0 Core + psycopg3** (sync). FastAPI endpoints are `async` and offload blocking DB/compute via `run_in_threadpool` (or a sync route). The worker is a plain sync process. Keep one engine/connection-pool factory in `kernel/config`.
- [ ] **CONV-09** **Every mutating operation passes through the security facade**: `authorize(principal, op, resource)` → do work → `audit(actor, op, resource, before, after, reason)`. No mutation bypasses authz+audit. (*Plan §3.1.4, §6*)
- [ ] **CONV-10** Logging: **structlog**, JSON renderer, with a **secret-redaction processor**. Never log secret values or resolved credentials. (*Plan §6.3, §1 observability*)
- [ ] **CONV-11** Errors: typed exception hierarchy in `keystone_contracts` (`KeystoneError`, `NotAuthorized`, `NotFound`, `ValidationError`, `PluginError`, `ConflictError`). API maps them to RFC-7807 `application/problem+json`.
- [ ] **CONV-12** Config via **pydantic-settings**, env-driven; `.env` for dev. Bake offline env vars into the default config: `HF_HUB_OFFLINE=1`, `TRANSFORMERS_OFFLINE=1`, DuckDB `extension_directory`, Tika/JRE paths, model dirs. (*Plan §11 D,G*)
- [ ] **CONV-13** **12-factor**: no local state beyond Postgres + the object store. Config from env. This is what makes the K8s move (Plan §9) free.
- [ ] **CONV-14** Tests: **pytest**. Every module ships unit tests; integration tests run against a real **local Postgres test database** and a **temp-dir filesystem store**. No network in tests (air-gap parity).
- [ ] **CONV-15** Quality gate (the "green gate"), run before finishing any step group: `ruff check` + `ruff format --check` + `mypy` + `lint-imports` (import-linter) + `pytest` — **all must pass**.
- [ ] **CONV-16** "Everything is a resource": new resource types add a row type over the single `resources` supertype and inherit authz/lineage/audit/search/health automatically. Never build a parallel permission/lineage system per type. (*Plan §3.5*)
- [ ] **CONV-17** Build the **narrowest contract** a phase actually needs; do not pre-build all 13 plugin hookspecs in Phase 0. Add each hookspec in the phase that first uses it. (*Plan §12 risk 1*)
- [ ] **CONV-18** Windows specifics: use `py -3.12`/`.venv\Scripts\activate`; set env vars via PowerShell (`$env:NAME="..."`); use `pathlib.Path` everywhere (never hardcode `/` or `\`). Default `FunctionRuntime` isolation = **subprocess**, not container. (*Plan §11 J*)

---

## 1. Phase −1 — Environment Preflight & Repo Scaffolding

### 1A. Verify the offline toolchain is present and working
- [ ] **ENV-01** Confirm **Python 3.12** (`py -3.12 --version`) and create the project venv: `py -3.12 -m venv .venv` then activate (`.venv\Scripts\activate`).
- [ ] **ENV-02** Confirm the **wheelhouse** is present; install build/runtime deps **offline only**: `pip install --no-index --find-links <wheelhouse> -r requirements.lock`. Assert no network was used.
- [ ] **ENV-03** Confirm **Node 20** (`node -v`) and the **npm cache / vendored node_modules** are present (Plan §11 C). Do a throwaway `npm ci --offline` in a temp dir to prove offline npm works.
- [ ] **ENV-04** Confirm **PostgreSQL 16** is installed and running; connect with `psql`. Confirm `pg_trgm` is available (`SELECT * FROM pg_available_extensions WHERE name='pg_trgm';`) and **pgvector is available** (`...WHERE name='vector';`) — needed from Phase 5 but verify now. (*Plan §11 B*)
- [ ] **ENV-05** Confirm **DuckDB** wheel imports (`python -c "import duckdb"`), and that the **offline extension directory** holds `delta`, `json`, `fts`, `vss`, `httpfs`, `excel` `.duckdb_extension` files matching the installed DuckDB version. (*Plan §11 D*)
- [ ] **ENV-06** Confirm staged later-phase software is on disk and note absolute paths: **Temurin JRE**, **Tika jar**, **Tesseract + tessdata**, **Ollama + model blobs**, **embedding model dir**, **MinIO (`minio.exe`,`mc.exe`)**, **Kafka tarball**, **MSVC Build Tools**. (*Plan §11 E–K*)
- [ ] **ENV-07** Decide whether **Docker/WSL2** is actually available on this box. Record the answer. If absent, the `container` FunctionRuntime stays unbuilt and `python_subprocess` is the only isolation. (*Plan §11 J*)
- [ ] **ENV-08** Create the local Postgres DB + role for the app and a separate **test** DB: `keystone`, `keystone_test`, role `keystone` with a password; store creds for the SecretStore master key separately.
- [ ] **ENV-09** Write a **PowerShell preflight script** `scripts/preflight.ps1` that re-checks ENV-01..ENV-08 and prints PASS/FAIL per item, so the environment can be re-validated any time.

### 1B. Repository scaffolding & tooling
- [ ] **SCAF-01** Initialize the repo: `git init` (if not already), add `.gitignore` (venv, `__pycache__`, `node_modules`, `dist`, `.env`, `*.duckdb`, data dirs).
- [ ] **SCAF-02** Create the directory tree exactly per Plan §2 (`src/keystone_contracts/`, `src/keystone/{kernel,services,plugins_builtin,api,worker}/...`, `ui/`, `tests/`, `migrations/`, `scripts/`).
- [ ] **SCAF-03** Write `pyproject.toml`: two packages (`keystone_contracts`, `keystone`), build backend `hatchling`, pinned deps mirroring the wheelhouse, and the **`[project.entry-points."keystone.plugins"]`** table (initially empty; appended to per plugin). (*Plan §3.4, §10*)
- [ ] **SCAF-04** Add tool configs: `ruff` (lint+format), `mypy` (strict on `keystone_contracts` and `kernel`), `pytest` (with `keystone_test` DB fixture), and `pre-commit` running the green gate.
- [ ] **SCAF-05** Add the **`import-linter`** contract file enforcing CONV-02 layering and "plugins → contracts only". Wire `lint-imports` into the gate. (*Plan §10*)
- [ ] **SCAF-06** Initialize **Alembic** (`migrations/`), point it at the config DB URL from settings, configure autogenerate off by default (write migrations explicitly). (*CONV-07*)
- [ ] **SCAF-07** `pip install -e .` (offline) and confirm `import keystone` / `import keystone_contracts` work.
- [ ] **SCAF-08** Create `ui/` with Vite + React + TypeScript + Blueprint scaffolding via the offline npm cache; confirm `npm run build` emits to `src/keystone/api/static/`. (*Plan §11 C*)
- [ ] **SCAF-09** Write `README.md` (run instructions) and `OFFLINE_BUNDLE.md` (the §11 checklist) at repo root. Keep `OFFLINE_BUNDLE.md` updated whenever a new dependency is introduced.
- [ ] **SCAF-GATE** Run the green gate (CONV-15). Commit scaffolding.

---

## 2. Phase 0 — Kernel & Plugin Spine
**Goal (Plan §8):** the skeleton everything hangs off. **Exit:** log in as a local user; create project/folder; see audit; a no-op plugin loads via entry points and shows in the Plugins admin view; the worker drains a trivial job.

### 2A. Contracts (build first — the stable spine)
- [ ] **P0-01** 🟦 `keystone_contracts`: base models — `Principal`, `ResourceRef`, `Operation` enum, `SecretHandle`, `Decision`, `SqlPredicate`, and the exception hierarchy (CONV-11). (*Plan §3.3, §6*)
- [ ] **P0-02** 🟦 `keystone_contracts`: the **plugin framework primitives** — a `PluginManifest` base (`id, display_name, type, api_version`), a `pluggy` `HookspecMarker/HookimplMarker` namespace (`keystone`), and a `WorkerContext` Protocol (CONV-04).
- [ ] **P0-03** 🟦 `keystone_contracts`: **AuthProvider** hookspec + Protocol (`authenticate`, `resolve_groups`, `issue_session`, `verify_session`) and `AuthProviderManifest`. (*Plan §6.1*)
- [ ] **P0-04** 🟦 `keystone_contracts`: **SecretStore** hookspec + Protocol (`put`, `resolve`) and `SecretStoreManifest`. (*Plan §6.3*)
- [ ] **P0-05** 🧪 Unit tests for contracts: manifests validate, Protocols are runtime-checkable, exception mapping table is complete.

### 2B. Core data model (migration 0001)
- [ ] **P0-06** 🟥 Migration `0001_core`: `resources` supertype (`id, type, parent_id, project_id, name, owner_group, created_by, created_at, updated_at, soft_deleted`). (*Plan §3.5*)
- [ ] **P0-07** 🟥 0001: security tables — `markings`, `resource_markings`, `principal_markings`, `roles`, `role_grants`. (*Plan §6.2*)
- [ ] **P0-08** 🟥 0001: identity tables — `users`, `groups`, `user_groups`, `service_accounts`, `sessions`. (*Plan §6.1*)
- [ ] **P0-09** 🟥 0001: `secrets` (sealed-box bytes + metadata) and `audit_events` (append-only). (*Plan §6.3*)
- [ ] **P0-10** 🟥 0001: `plugins` (id, type, version, status[active|quarantined|disabled], source_package, error). (*Plan §3.4*)
- [ ] **P0-11** 🟥 0001: run/queue/event/lineage tables — `runs`, `run_events`, `jobs` (queue), `events`, `lineage_edges`. (*Plan §3.1.3, §3.1.5, §3.1.6*)
- [ ] **P0-12** ✅ `alembic upgrade head` then `downgrade base` both succeed on a clean DB.

### 2C. Kernel
- [ ] **P0-13** 🟦 `kernel/config`: settings (pydantic-settings), SQLAlchemy engine/session factory, DI container, **`WorkerContext` factory**, structlog setup + redaction processor. (*CONV-08, CONV-10, CONV-12*)
- [ ] **P0-14** 🟦 `kernel/resources`: `new_id()` util + resource graph CRUD (create/get/list/move/soft-delete, parent/child, ownership, attach/detach markings). (*Plan §3.1.1, CONV-05*)
- [ ] **P0-15** 🟦 `kernel/plugins/host.py`: entry-point **discovery** (`keystone.plugins`), **manifest validation** (Pydantic), `api_version` compat gate, `pluggy` PluginManager registration, **capability index** (capability→[ids]), **quarantine** on failure (write to `plugins` table, never crash), **kill-switch** (disable by id). (*Plan §3.4*)
- [ ] **P0-16** 🟦 `kernel/security`: **AuthProvider facade** (delegates to active provider plugin), **Authorizer** (roles + markings now; `object_predicate`/`visible_properties` return permissive stubs until Phase 3), **SecretStore facade**, **audit writer**. Expose `authorize()` + `audit()` (CONV-09). (*Plan §6*)
- [ ] **P0-17** 🟦 `kernel/runs`: `enqueue(job)`, the **`SELECT … FOR UPDATE SKIP LOCKED`** dequeue, run ledger + state machine (`queued→running→succeeded|failed|cancelled`), `run_events` append. (*Plan §1, §3.1.3*)
- [ ] **P0-18** 🟦 `kernel/events`: in-proc synchronous bus (`emit`/subscribe) backed by the durable `events` table (replayable). (*Plan §3.1.6*)
- [ ] **P0-19** 🟦 `kernel/lineage`: `record(edge)` append + recursive-CTE traversal queries (upstream/downstream). (*Plan §3.1.5*)
- [ ] **P0-20** 🟦 `worker/`: the worker entrypoint that runs `runs.worker_loop()` (poll → claim → execute handler → record). Same package, second process. (*Plan §2*)
- [ ] **P0-21** 🧪 Kernel tests: resource CRUD + markings; plugin host **discovers a built-in and quarantines a deliberately-broken plugin**; authorizer allow/deny on roles+markings; queue concurrency (two workers, no double-claim via SKIP LOCKED); event durability; lineage traversal.

### 2D. Day-one plugins
- [ ] **P0-22** 🟩 `plugins_builtin/auth/local`: `users/groups/service_accounts`, **Argon2id** hashing, session issue/verify (signed token or DB session), seeded **admin** on first run. Register entry point. (*Plan §6.1*)
- [ ] **P0-23** 🟩 `plugins_builtin/secrets/local_encrypted`: **libsodium sealed box** (pynacl) in the `secrets` table; master key from env/OS keyring; `resolve()` only inside a scoped `WorkerContext`. Register entry point. (*Plan §6.3*)
- [ ] **P0-24** 🟩 `plugins_builtin/_noop_example`: a trivial no-op plugin used to prove the discovery path end-to-end (kept as a template). Register entry point.
- [ ] **P0-25** 🧪 Plugin tests: local auth (login success/fail, session verify, password hashing); secrets (put/resolve round-trip, value never appears in logs); no-op plugin appears in capability index + `plugins` table.

### 2E. API
- [ ] **P0-26** 🟨 `api/`: FastAPI app factory, problem+json exception handlers (CONV-11), session/auth dependency that resolves a `Principal`, static-asset mounting for the built UI.
- [ ] **P0-27** 🟨 Routers: `auth` (`POST /login`, `POST /logout`, `GET /me`), `resources` (CRUD for **project** and **folder** resource types), `plugins` (`GET /plugins` list + status), `audit` (`GET /audit` filtered), `system` (`GET /healthz`, `GET /version`).
- [ ] **P0-28** 🧪 API smoke tests (httpx test client): login → me → create project → create folder under it → list plugins → read audit; unauthenticated requests are rejected.

### 2F. UI
- [ ] **P0-29** 🟪 App frame: Blueprint dark theme, top bar, **persistent left resource-navigation tree**, content area, right config panel slot. (*Plan §1 frontend*)
- [ ] **P0-30** 🟪 **Login page** wired to `/login`; auth state + TanStack Query client; logout.
- [ ] **P0-31** 🟪 **Generic resource-detail layout** with tabs: Overview / Schema / Runs / Lineage / Health / Permissions / Audit — reused by ALL resource types in later phases (build the shell now). (*Plan §12 risk 8*)
- [ ] **P0-32** 🟪 **Plugins admin view** (lists installed plugins, type, version, status, owner package; kill-switch toggle) and **Audit view**.
- [ ] **P0-33** 🟪 Project/folder create + tree browse wired to `/resources`. `npm run build` → static assets served by the API.

### 2G. Gate & Exit
- [ ] **P0-GATE** Run the green gate (CONV-15). Fix all failures.
- [ ] **P0-EXIT-1** ✅ Start Postgres, launch **API + worker**; log in as the seeded admin.
- [ ] **P0-EXIT-2** ✅ Create a project and a folder; confirm both appear in the tree and produce **audit events**.
- [ ] **P0-EXIT-3** ✅ The no-op plugin **loads via entry points** and appears in the Plugins admin view; toggling the kill-switch flips its status.
- [ ] **P0-EXIT-4** ✅ Enqueue a trivial job; the **worker drains it**; run + run_events recorded.
- [ ] **P0-EXIT-5** ✅ Deliberately break a plugin manifest → it is **quarantined** with an error, kernel still boots. Revert.
- [ ] **P0-EXIT-6** Commit Phase 0.

---

## 3. Phase 1 — Data Connection + Datasets
**Goal:** ingest real data, versioned, with lineage. **Exit:** batch-sync a Postgres table into a Delta dataset; drag-drop a CSV; preview rows; a failed sync commits nothing; transaction history + source→dataset lineage visible.

### 3A. Contracts & migration
- [ ] **P1-01** 🟦 Contracts: **Connector** hookspec/Protocol (`test`, `explore`, `sync`) + `ConnectorManifest` (capabilities enum, `config_schema`, `supported_auth`). (*Plan §3.3*)
- [ ] **P1-02** 🟦 Contracts: **StorageBackend** Protocol (`put/get/list/presign`) + manifest. (*Plan §3.2*)
- [ ] **P1-03** 🟦 Contracts: **DatasetBackend** Protocol (`begin/write/commit/abort/scan/schema/history`, `TxnType`, `CommitInfo`) + manifest. (*Plan §3.3*)
- [ ] **P1-04** 🟦 Contracts: **Scheduler/Trigger** Protocol (`manual`,`cron`,`on_input_update`) + manifest.
- [ ] **P1-05** 🟥 Migration `0002_data_connection`: `sources`, `syncs`, `datasets` (resource subtype: `backend_id`, `current_version`, `schema_id`, `row_count`, `storage_uri`), `dataset_transactions` (version pointer + summary → authoritative `_delta_log`), `schedules`, `source_secret_refs`. (*Plan §4, §5.1*)

### 3B. Services & query engine
- [ ] **P1-06** 🟦 `services/query`: **DuckDB session manager** (configured for offline extensions per ENV-05); helpers to scan Parquet/Delta/CSV and return Arrow. Wire as a **direct internal seam**, NOT a plugin. (*Plan §3.2, §12 risk 2*)
- [ ] **P1-07** 🟦 `services/data_connection`: source catalog (create/test/explore), **capability dispatch** (resolve `connector_id` → hookimpl, invoke with `WorkerContext`), sync orchestration (enqueue sync job → worker runs connector → stages Arrow → commits via DatasetBackend).
- [ ] **P1-08** 🟦 `services/datasets`: dataset lifecycle, transaction commit/abort, **atomicity guarantee** (a failed sync aborts the txn → no partial trusted data), history, schema, preview (via DuckDB). (*Plan §4*)
- [ ] **P1-09** 🟦 Lineage emission: every sync/commit emits `source→dataset` edges via `kernel.lineage`. (*Plan §3.1.5*)

### 3C. Plugins
- [ ] **P1-10** 🟩 `storage/fs`: filesystem StorageBackend (path-safe via `pathlib`). (*Plan §11 default*)
- [ ] **P1-11** 🟩 `dataset/delta`: delta-rs (`deltalake`) backend — ACID commit, MERGE/UPDATE/DELETE, time-travel (`load_version`/`load_as_of`), schema evolution; Postgres stores only the pointer/summary. (*Plan §1, §4*)
- [ ] **P1-12** 🟩 `dataset/parquet_snapshot`: trivial immutable-snapshot backend for uploads/previews. (*Plan §4*)
- [ ] **P1-13** 🟩 `connectors/postgres`: `test/explore/batch_sync` (+ `incremental_sync` cursor stub for Phase 3-readiness) via psycopg; outputs Arrow batches.
- [ ] **P1-14** 🟩 `connectors/file`: read CSV/Parquet/JSON from a path/StorageBackend; schema inference via DuckDB.
- [ ] **P1-15** 🟩 `connectors/rest`: HTTP client, pagination templates, OAuth2/token via SecretStore; JSON→Arrow.
- [ ] **P1-16** 🟩 `connectors/upload`: browser multipart upload → `parquet_snapshot` dataset; schema inference.
- [ ] **P1-17** 🟩 `schedulers/manual` + `schedulers/cron`. Register all entry points (P1-10..P1-17) in `pyproject.toml`.
- [ ] **P1-18** 🧪 Plugin/integration tests: delta commit + time-travel + abort-leaves-no-version; each connector `test/explore/sync` against local fixtures; upload round-trip; cron schedule fires a job.

### 3D. API & UI
- [ ] **P1-19** 🟨 Routers: `sources` (CRUD, test, explore), `syncs` (create/run/cancel/status), `datasets` (get, schema, **preview**, transactions/history, lineage), `uploads`.
- [ ] **P1-20** 🟪 **Data Connection** screen: source catalog (pick connector → config form generated from `config_schema` → test → explore tree), create sync, run + watch status.
- [ ] **P1-21** 🟪 **Dataset** detail (reusing the §P0-31 layout): Overview, **Schema** tab, **Runs** tab (sync history), **Transactions** (versions/time-travel), **preview** grid (TanStack Table), **Lineage** tab (React Flow source→dataset). Drag-and-drop CSV upload.
- [ ] **P1-22** 🧪 API tests for all P1-19 routes incl. failure paths.

### 3E. Gate & Exit
- [ ] **P1-GATE** Green gate.
- [ ] **P1-EXIT-1** ✅ Batch-sync a local Postgres table → **Delta dataset**; preview rows; history shows v0.
- [ ] **P1-EXIT-2** ✅ Drag-drop a CSV → snapshot dataset; preview rows.
- [ ] **P1-EXIT-3** ✅ Kill a sync mid-run → assert **no partial transaction committed** (version unchanged).
- [ ] **P1-EXIT-4** ✅ Dataset **Lineage** tab shows source→dataset; **Transactions** tab shows commits.
- [ ] **P1-EXIT-5** Commit Phase 1.

---

## 4. Phase 2 — Pipelines + Validity + Health
**Goal:** transform and trust data. **Exit:** build raw→curated pipeline in the UI, preview each node; a PK/row-count check blocks publish; Content-Validity vs Operational-Health tabs both populated; lineage spans source→raw→pipeline→curated.

### 4A. Contracts & migration
- [ ] **P2-01** 🟦 Contracts: **TransformNode** Protocol (`infer_schema`, `to_sql`, `execute`) + `NodeManifest` (node_type, inputs, params_schema). (*Plan §3.3*)
- [ ] **P2-02** 🟦 Contracts: **ValidityCheck** Protocol (`evaluate → CheckResult`) + `CheckManifest`. (*Plan §3.3*)
- [ ] **P2-03** 🟥 Migration `0003_pipelines_health`: `pipelines`, `pipeline_graph` (nodes+edges as validated JSON or normalized tables), `validity_contracts`, `validity_checks`, `validity_results` (with sample-rows ref), `monitors`, `health_issues` (status, freshness, assignment, snooze). **Keep content-validity and operational-health as separate tables/surfaces.** (*Plan §1, §8*)

### 4B. Services
- [ ] **P2-04** 🟦 `services/pipelines`: graph model + validation (DAG, type-checked ports), **compile** to an execution plan, **per-node `infer_schema`** for live preview, executor (DuckDB SQL pushdown via `to_sql`; Polars/Python fallback via `execute`). (*Plan §1, §3.2*)
- [ ] **P2-05** 🟦 `services/pipelines`: outputs commit to a **curated DatasetBackend** txn; emit transform lineage edges (input ds → node → output ds).
- [ ] **P2-06** 🟦 `services/validity`: contracts + **enforcement modes** (block-publish vs warn); runs checks on commit; writes `validity_results`/issues. (*Plan §1*)
- [ ] **P2-07** 🟦 `services/health`: monitors (status/freshness/row-count drift), **issue lifecycle** (open/ack/snooze/assign/resolve), distinct from validity. (*Plan §1, §8*)

### 4C. Plugins
- [ ] **P2-08** 🟩 Nodes: `select`, `filter`, `join`, `union`, `aggregate`, `cast`, `parse_json`, `dedupe`, and `python` (escape hatch). Prefer `to_sql` pushdown; `python` uses `execute`. (*Plan §8 Phase 2*)
- [ ] **P2-09** 🟩 Checks: `not_null`, `unique_pk`, `enum`, `regex`, `row_count`, `referential`. Register all P2-08/P2-09 entry points.
- [ ] **P2-10** 🧪 Tests: each node `infer_schema` + execute (SQL and fallback); each check pass/fail with sample rows; a failing `unique_pk` blocks publish; lineage spans transforms.

### 4D. API & UI
- [ ] **P2-11** 🟨 Routers: `pipelines` (CRUD, validate, **preview node**, run, publish), `validity` (contracts CRUD, results), `health` (monitors CRUD, issues + lifecycle actions).
- [ ] **P2-12** 🟪 **Pipeline Builder** (React Flow): node palette from the node registry, drag/connect, config panels from `params_schema`, **live per-node preview** grids, run + publish.
- [ ] **P2-13** 🟪 **Data Health** screen with two clearly separated tabs: **Content Validity** (contract violations) and **Operational Health** (freshness/status/abnormality), plus issue lifecycle controls. (*Plan §1, §8*)
- [ ] **P2-14** 🟪 Extend dataset/pipeline **Lineage** tab to render the full source→raw→pipeline→curated graph.
- [ ] **P2-15** 🧪 API tests for all P2-11 routes.

### 4E. Gate & Exit
- [ ] **P2-GATE** Green gate.
- [ ] **P2-EXIT-1** ✅ Build a raw→curated pipeline in the UI; **preview each node**.
- [ ] **P2-EXIT-2** ✅ A `unique_pk`/`row_count` check **fails → publish blocked**; a Content-Validity issue appears.
- [ ] **P2-EXIT-3** ✅ Operational-Health tab populates (freshness/status) **separately** from validity.
- [ ] **P2-EXIT-4** ✅ Lineage spans source→raw→pipeline→curated.
- [ ] **P2-EXIT-5** Commit Phase 2.

---

## 5. Phase 3 — Ontology (the differentiator)
**Goal:** a live, permissioned semantic API. **Exit:** map a curated dataset → `Customer` object type with PK; define `Customer→Order` link; object query returns only authorized objects (markings + object policy enforced **in SQL**); graph traversal works; ontology lineage visible.

### 5A. Contracts & migration
- [ ] **P3-01** 🟦 Contracts: **ObjectIndex** Protocol (`upsert`, `delete`, `query(q, principal)` — **must inject authz predicate**) + `ObjectIndexManifest` (capability: relational|search|vector|graph). (*Plan §3.3, §5.2*)
- [ ] **P3-02** 🟦 Contracts: `ObjectQuery`/`ObjectPage` models (filter/sort/paginate/search/vector/traverse params).
- [ ] **P3-03** 🟥 Migration `0004_ontology_types`: `ontology_versions`, `object_types`, `object_properties`, `shared_properties`, `value_types`, `interfaces`, `link_types`. (*Plan §5.1*)
- [ ] **P3-04** 🟥 Migration `0005_object_security`: `object_policies` (row predicate template), `property_policies` (column projection). Upgrade the Authorizer stubs from P0-16 to real `object_predicate`/`visible_properties`. (*Plan §6.2*)

### 5B. Services — the materializer (centerpiece)
- [ ] **P3-05** 🟦 `services/ontology`: type management (CRUD for object/link/value/shared/interfaces, draft→published versions, PK declaration + validation: unique/non-null/stable). (*Plan §5.1*)
- [ ] **P3-06** 🟦 `services/ontology/materializer.py`: **dynamic DDL** to create `obj_<api_name>` (pk PK, `properties jsonb`, promoted indexed columns, `search_tsv tsvector GENERATED`, `embedding vector(N) NULL` (nullable now), `_src_dataset_version`, `_row_refs jsonb`, `_markings int[]`) + indexes (GIN tsv, btree promoted, GIN `_markings`; HNSW deferred to Phase 5). (*Plan §5.2*)
- [ ] **P3-07** 🟦 Materialization flow: curated Delta → DuckDB read → map columns→properties → **ontology validity** (PK unique/non-null, links resolve) → `ObjectIndex.relational.upsert` → generated `search_tsv` → emit `dataset→object_type` lineage → record run. Modes: snapshot / incremental_append / merge-by-PK, on the **worker**. (*Plan §5.3*)
- [ ] **P3-08** 🟦 Links: derived links as VIEW over FKs; mapped links as `link_<name>` table; cardinality enforcement. (*Plan §5.2*)
- [ ] **P3-09** 🟦 **Security in the query path**: every `ObjectIndex.query` appends `AND has_access(_markings, principal) AND <object_policy predicate>` and **projects out** properties the principal can't see (property policies). Implement `has_access` as a SQL helper. (*Plan §5.2, §6.2*)
- [ ] **P3-10** 🟦 **Marking propagation**: output markings = union of input markings (minus authorized declassification), written to `resource_markings`/row `_markings` during materialization. (*Plan §6.4*)

### 5C. Plugins
- [ ] **P3-11** 🟩 `indexes/relational` (filter/sort/paginate + point lookup), `indexes/search` (`search_tsv @@ websearch_to_tsquery`), `indexes/graph` (recursive-CTE neighborhood/path). `indexes/vector` = **stub** (activated Phase 5). Register entry points. (*Plan §5.2*)
- [ ] **P3-12** 🧪 Tests: materialize a dataset→object type (snapshot + incremental + merge); PK violation blocks materialization; relational/search/graph queries; **authz: a restricted principal sees fewer rows and null'd columns — assert at the SQL level**; marking union propagation.

### 5D. API & UI
- [ ] **P3-13** 🟨 Routers: `ontology` (types CRUD, versions, publish), `objects` (`query`/get/search/aggregate), `links` (traverse/search-around), `object-policies`/`property-policies` CRUD.
- [ ] **P3-14** 🟪 **Ontology Manager**: define object types (map dataset columns→properties, set PK, mark indexed/search), link types, value types, interfaces; trigger materialization; view object/property security policies.
- [ ] **P3-15** 🟪 **Object Explorer**: search/filter object sets, table + detail views, **graph traversal** ("search around") via React Flow; object **Object View** (Overview/properties/links tabs).
- [ ] **P3-16** 🟪 Permissions tab on object types: markings, object policies (row), property policies (column).
- [ ] **P3-17** 🧪 API tests incl. authz-filtered object queries for two different principals.

### 5E. Gate & Exit
- [ ] **P3-GATE** Green gate.
- [ ] **P3-EXIT-1** ✅ Map a curated dataset → `Customer` object type with a valid PK; materialize it.
- [ ] **P3-EXIT-2** ✅ Define a `Customer→Order` link; traverse it in the UI.
- [ ] **P3-EXIT-3** ✅ As a restricted user, an object query **returns only authorized objects and nulls restricted properties — enforced in SQL** (verify the generated query).
- [ ] **P3-EXIT-4** ✅ Ontology lineage (dataset→object_type) visible.
- [ ] **P3-EXIT-5** Commit Phase 3.

---

## 6. Phase 4 — Actions & Functions (kinetics / writeback)
**Goal:** change the world, audited. **Exit:** a permissioned, audited action edits an object; a function-backed action; a webhook effect with an idempotency key.

### 6A. Contracts & migration
- [ ] **P4-01** 🟦 Contracts: **FunctionRuntime** Protocol (execute with I/O contract + sandbox) + manifest. (*Plan §3.2*)
- [ ] **P4-02** 🟦 Contracts: **ActionHandler/Effect** Protocol (one side-effect; idempotency key support) + manifest. (*Plan §3.2*)
- [ ] **P4-03** 🟥 Migration `0006_actions_functions`: `action_types` (parameters schema, submission criteria, before/after audit config), `function_defs` (runtime_id, signature, code_ref, returns), `action_executions` (idempotency keys, status). (*Plan §5.1, §6.3*)

### 6B. Services
- [ ] **P4-04** 🟦 `services/functions`: function registry, validation, invocation via FunctionRuntime; functions can **read the ontology** (objects/links) through a scoped, authz-checked API. (*Plan §7 read/write*)
- [ ] **P4-05** 🟦 `services/actions`: action execution pipeline — validate parameters → check **submission criteria** → authorize → run effects (transactional) → **write before/after to `audit_events`** → emit ontology-edit writeback to the backing dataset. (*Plan §6, §7*)
- [ ] **P4-06** 🟦 **Function-backed actions**: an action whose logic is a function; **idempotency** enforced on effects.

### 6C. Plugins
- [ ] **P4-07** 🟩 `runtimes/python_inproc` and `runtimes/python_subprocess` (default isolation; container deferred per ENV-07). (*Plan §11 J*)
- [ ] **P4-08** 🟩 `effects/ontology_edit` (writes object/property/link edits → writeback dataset → re-materialize) and `effects/webhook` (HTTP call, secret via SecretStore, **idempotency key**, retries). Register entry points.
- [ ] **P4-09** 🧪 Tests: action edits an object (authz + before/after audit asserted); submission criteria rejects bad input; function-backed action; webhook effect **runs once for a repeated idempotency key**; subprocess isolation.

### 6D. API & UI
- [ ] **P4-10** 🟨 Routers: `actions` (types CRUD, **execute**), `functions` (CRUD, test-invoke), `action-executions` (history).
- [ ] **P4-11** 🟪 Action type editor (parameters form, submission criteria, effects), action **execution UI** (form → submit → result), function editor (Monaco), and an **Audit** tab showing before/after for each action.
- [ ] **P4-12** 🧪 API tests for all P4-10 routes.

### 6E. Gate & Exit
- [ ] **P4-GATE** Green gate.
- [ ] **P4-EXIT-1** ✅ Define + execute a **permissioned, audited** action that edits an object property; before/after in `audit_events`.
- [ ] **P4-EXIT-2** ✅ A **function-backed** action works.
- [ ] **P4-EXIT-3** ✅ A **webhook effect** with an idempotency key fires once on duplicate submit.
- [ ] **P4-EXIT-4** Commit Phase 4.

---

## 7. Phase 5 — Media, Search & Embeddings
**Goal:** unstructured data + semantic search. **Exit:** upload PDFs → searchable chunks → Document objects → semantic search returns chunks.

### 7A. Prereqs, contracts & migration
- [ ] **P5-01** ✅ Confirm Phase-5 software paths (Tika jar + JRE, Tesseract + tessdata, embedding model dir) and offline env vars from ENV-06/CONV-12.
- [ ] **P5-02** 🟥 Enable **pgvector**: `CREATE EXTENSION vector;` migration; add **HNSW index** on `obj_*.embedding`; activate the `vector` ObjectIndex (replace the P3-11 stub). (*Plan §11 B, §5.2*)
- [ ] **P5-03** 🟥 Migration `0007_media`: `media_sets`, `media_items` (refs to StorageBackend blobs, extraction status/confidence).
- [ ] **P5-04** 🟦 Contracts: extend nodes for `ocr`, `chunk`, `embed`, and (optional) `llm` (added fully in Phase 6).

### 7B. Services & plugins
- [ ] **P5-05** 🟦 `services` media pipeline: ingest → Tika parse → OCR (Tesseract) when needed → chunk → embed → write Document/DocumentChunk **object types** (ordinary object types, no special-casing) + vector index. (*Plan §5.2, §7*)
- [ ] **P5-06** 🟩 Nodes: `ocr` (Tesseract via `pytesseract`), `chunk` (configurable splitter), `embed` (local sentence-transformers/ONNX, offline). Register entry points.
- [ ] **P5-07** 🟦 Wire **semantic search** into the object API (`vector` index `ORDER BY embedding <=> $q`), respecting the same authz predicate. (*Plan §5.2, §6.2*)
- [ ] **P5-08** 🧪 Tests (with small fixture PDFs/images, fully offline): parse→OCR→chunk→embed; vector query returns relevant chunks; authz still applied to chunk objects.

### 7C. API, UI, Gate & Exit
- [ ] **P5-09** 🟨 Routers: `media` (sets/items, upload), `search` (semantic + keyword).
- [ ] **P5-10** 🟪 Media set UI (upload, status), and **semantic search** in Object Explorer (toggle keyword/semantic).
- [ ] **P5-11** 🟪 Document object views showing extracted text, chunks, and source media refs.
- [ ] **P5-GATE** Green gate.
- [ ] **P5-EXIT-1** ✅ Upload PDFs → searchable chunks → Document objects.
- [ ] **P5-EXIT-2** ✅ **Semantic search** returns relevant chunks; authz enforced.
- [ ] **P5-EXIT-3** Commit Phase 5.

---

## 8. Phase 6 — Models & ML (+ optional LLM / AIP-assist)
**Goal:** Palantir/Dataiku-style trainable models. **Exit:** train + register a model with metrics; score it in a pipeline (node) and online (function); (optional) an `llm` node classifies rows.

### 8A. Contracts & migration
- [ ] **P6-01** 🟦 Contracts: **ModelRuntime** Protocol (`train → ModelArtifactRef`, `evaluate → Metrics`, `predict`) + manifest. (*Plan §3.3, §7*)
- [ ] **P6-02** 🟦 Contracts: **ModelProvider (LLM)** Protocol (text gen + embeddings) + manifest. (*Plan §3.2*)
- [ ] **P6-03** 🟥 Migration `0008_models`: `models` (resource subtype, runtime_id), `model_versions` (artifact ref via StorageBackend, metrics, training-dataset lineage), `training_runs` (reuse `runs`). (*Plan §7*)

### 8B. Services & plugins
- [ ] **P6-04** 🟦 `services/models`: model registry, **training as a worker job** (reads a dataset, writes a versioned artifact + metrics, emits lineage), evaluation, version management. (*Plan §7*)
- [ ] **P6-05** 🟦 Scoring exposed **two ways**: a `model_predict` **TransformNode** (batch) and a **scoring Function** (online for actions/object views). (*Plan §7*)
- [ ] **P6-06** 🟩 `modelruntimes/sklearn` and `modelruntimes/xgboost` (CPU; `lightgbm`/`pytorch` optional). Register entry points.
- [ ] **P6-07** 🟩 (Optional) `modelproviders/ollama` (local LLM) + `nodes/llm` (classify/extract/summarize over rows) + an **AIP-assist** helper endpoint; all offline. (*Plan §7, §11 G*)
- [ ] **P6-08** 🟦 (Optional) **JupyterLab** integration for code-first modeling (Foundry Code Workspaces / Dataiku notebooks analog), reading/writing datasets + ontology under the same authz. (*Plan §7, §11 H*)
- [ ] **P6-09** 🧪 Tests: train→register→evaluate (sklearn + xgboost) with metrics + lineage; `model_predict` node scores a dataset; scoring function returns predictions online; (optional) `llm` node classifies fixtures offline.

### 8C. API, UI, Gate & Exit
- [ ] **P6-10** 🟨 Routers: `models` (CRUD, **train**, versions, metrics, predict), and (optional) `assist`.
- [ ] **P6-11** 🟪 Model UI: configure training (algorithm + dataset + target + params), launch training, view versions + metrics, use `model_predict` in the Pipeline Builder, attach a scoring function to an action/object view. (Optional Dataiku-style guided/AutoML config over the same ModelRuntime.)
- [ ] **P6-GATE** Green gate.
- [ ] **P6-EXIT-1** ✅ Train a model on a dataset; **register a version with metrics**.
- [ ] **P6-EXIT-2** ✅ Score it **in a pipeline (node)** and **online (function)**.
- [ ] **P6-EXIT-3** ✅ (If built) an `llm` node classifies rows fully offline.
- [ ] **P6-EXIT-4** Commit Phase 6.

---

## 9. Phase 7 — Streaming / CDC + Externalize for Kubernetes
**Goal:** low-latency ingestion (still single-machine), then flip the production seams. **Exit:** a topic micro-batches into a dataset with lag in Health; the **same images** run on a K8s namespace with S3 + Okta.

### 9A. Streaming / CDC
- [ ] **P7-01** 🟦 Contracts: add streaming capabilities to the Connector contract (`streaming_sync`, `cdc_sync`); offset/cursor model.
- [ ] **P7-02** 🟥 Migration `0009_streaming`: `streams`, `stream_offsets`.
- [ ] **P7-03** 🟩 `connectors/kafka` (client per Plan §11 I) + **micro-batch CDC** consumer on the worker (Debezium-format aware); commit micro-batches as dataset APPEND txns. (*Plan §8 Phase 7*)
- [ ] **P7-04** 🟦 `services/health`: **stream freshness/lag** monitors. (*Plan §8*)
- [ ] **P7-05** 🧪 Tests: micro-batch a local topic → dataset APPEND; lag monitor populates. (Use Kafka-on-JRE; no broker needed for DB CDC.)
- [ ] **P7-06** 🟪 Stream UI: source config + lag in the Data Health screen.

### 9B. Production seams (no kernel/services changes — only new plugins + config)
- [ ] **P7-07** 🟩 `storage/s3` (or `minio`) StorageBackend; switch via `backend_id`/config. (*Plan §1, §9*)
- [ ] **P7-08** 🟩 `auth/oidc` (Okta) AuthProvider — same Protocol as `local`; switch the active provider in config; map IdP claims→groups. **Verify nothing downstream changed.** (*Plan §6.1, §9*)
- [ ] **P7-09** 🟩 `secrets/vault` SecretStore (optional) and a `RemoteAuthorizer` backed by **OpenFGA/OPA** (optional) — same interfaces as in-proc. (*Plan §6.2–6.3, §9*)
- [ ] **P7-10** 🟦 Containerize: two images (**api**, **worker**) from one package; 12-factor config; healthchecks. (*Plan §9*)
- [ ] **P7-11** 🟦 K8s manifests/Helm: api + worker Deployments, Postgres (managed/StatefulSet), object store (S3/MinIO), config/secrets, ingress. (*Plan §9*)
- [ ] **P7-12** 🟦 (Optional) OTel exporters → Prometheus/Loki/Tempo, behind the existing observability seam. (*Plan §9*)

### 9C. Gate & Exit
- [ ] **P7-GATE** Green gate.
- [ ] **P7-EXIT-1** ✅ A Kafka topic **micro-batches into a dataset** with lag visible in Data Health.
- [ ] **P7-EXIT-2** ✅ The **same api/worker images** run on a K8s namespace with `s3` storage + `okta` OIDC — **without changing kernel or services**, only plugins + config.
- [ ] **P7-EXIT-3** Commit Phase 7.

---

## 10. Final Acceptance — Definition of Done (whole platform)
- [ ] **DONE-01** ✅ End-to-end demo: source → raw dataset → pipeline → curated dataset → object type → link → action (audited) → model scoring → semantic search, all under one authz/lineage/audit spine.
- [ ] **DONE-02** ✅ Plan §13 verification scenarios for every phase pass and are scripted as repeatable tests.
- [ ] **DONE-03** ✅ The **13 plugin types** each have ≥1 working implementation registered via entry points; the Plugins admin view lists them with owners. (*Plan §3.2*)
- [ ] **DONE-04** ✅ `import-linter` proves the layering (CONV-02); a fuzzed/broken plugin is quarantined, never crashes the kernel.
- [ ] **DONE-05** ✅ Security: markings propagate by union through lineage; object/property policies enforced in SQL; secrets never logged; every mutation audited.
- [ ] **DONE-06** ✅ Air-gap proof: a clean run on the offline box with the network physically disabled completes Phases 0–6 (DuckDB extensions, models, Tika, Tesseract all load locally). (*Plan §12 risk 9*)
- [ ] **DONE-07** ✅ Dev→prod proof: the K8s deployment runs with S3 + Okta with zero kernel/services edits. (*Plan §9*)
- [ ] **DONE-08** ✅ `README.md` + `OFFLINE_BUNDLE.md` are current; `scripts/preflight.ps1` passes; a fresh checkout can be built offline from the docs alone.

---

## 11. Appendix A — Plugin Entry-Point Registry Checklist
Confirm each is registered under `[project.entry-points."keystone.plugins"]` and visible in the Plugins admin view:
- [ ] **REG-auth** `auth/local` · (P7) `auth/oidc`
- [ ] **REG-secrets** `secrets/local_encrypted` · (P7) `secrets/vault`
- [ ] **REG-storage** `storage/fs` · (P7) `storage/s3`|`minio`
- [ ] **REG-dataset** `dataset/delta`, `dataset/parquet_snapshot`
- [ ] **REG-connector** `connectors/{postgres,rest,file,upload}` · (P7) `connectors/kafka`
- [ ] **REG-scheduler** `schedulers/{manual,cron}` · (later) `on_input_update`
- [ ] **REG-node** `nodes/{select,filter,join,union,aggregate,cast,parse_json,dedupe,python,model_predict}` · (P5) `ocr,chunk,embed` · (P6) `llm`
- [ ] **REG-check** `checks/{not_null,unique_pk,enum,regex,row_count,referential}`
- [ ] **REG-index** `indexes/{relational,search,graph}` · (P5) `vector`
- [ ] **REG-effect** `effects/{ontology_edit,webhook}`
- [ ] **REG-runtime** `runtimes/{python_inproc,python_subprocess}` · (opt) `container`
- [ ] **REG-modelruntime** `modelruntimes/{sklearn,xgboost}` · (opt) `lightgbm,pytorch`
- [ ] **REG-modelprovider** (opt) `modelproviders/ollama`

## 12. Appendix B — Migration Order Checklist
- [ ] **MIG** `0001_core` → `0002_data_connection` → `0003_pipelines_health` → `0004_ontology_types` → `0005_object_security` → `0006_actions_functions` → `0007_media` → (`vector` enable) → `0008_models` → `0009_streaming`. Each has a tested `upgrade` **and** `downgrade`.

## 13. Appendix C — Per-Phase Ritual (do this for EVERY phase)
- [ ] **RITUAL-1** Add/extend the **narrowest contracts** the phase needs (CONV-17).
- [ ] **RITUAL-2** Write the **migration(s)**; test upgrade+downgrade (CONV-07).
- [ ] **RITUAL-3** Implement **services**, then **plugins**, registering entry points (CONV-03).
- [ ] **RITUAL-4** Add **API routes** + **UI**; `npm run build`.
- [ ] **RITUAL-5** Write **unit + integration tests**; keep them offline (CONV-14).
- [ ] **RITUAL-6** Run the **green gate** (CONV-15); fix everything.
- [ ] **RITUAL-7** Run the phase **EXIT** checks; demo them.
- [ ] **RITUAL-8** Update `README`/`OFFLINE_BUNDLE`; **commit** referencing step IDs.
