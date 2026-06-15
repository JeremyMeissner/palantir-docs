# Palantir-Inspired Data Connector And Data Health Architecture

Status: architecture draft  
Scope: connection, data transfer, storage, health, ontology mapping, and required technologies.  
Non-goal: detailed UX copy, visual branding, or workflow implementation.

## Source Material

This architecture is inspired by public Palantir Foundry concepts and adapts them into an independent system:

- [Data Connection core concepts](https://www.palantir.com/docs/foundry/data-connection/core-concepts/)
- [Data Connection architecture examples](https://www.palantir.com/docs/foundry/data-connection/architecture/)
- [Batch sync setup](https://www.palantir.com/docs/foundry/data-connection/set-up-sync/)
- [Streaming sync setup](https://www.palantir.com/docs/foundry/data-connection/set-up-streaming-sync/)
- [Foundry datasets](https://www.palantir.com/docs/foundry/data-integration/datasets/)
- [File-based syncs](https://www.palantir.com/docs/foundry/data-connection/file-based-syncs/)
- [Data Health and health checks](https://www.palantir.com/docs/foundry/health-checks/overview/)
- [Monitoring views](https://www.palantir.com/docs/foundry/monitoring-views/overview/)
- [Observability overview](https://www.palantir.com/docs/foundry/observability/overview/)
- [Object types](https://www.palantir.com/docs/foundry/object-link-types/object-types-overview/)
- [Link types](https://www.palantir.com/docs/foundry/object-link-types/link-types-overview/)

## Product Shape

Build a Palantir-like operational data platform with five first-class applications sharing one resource graph:

1. **Data Connection**: sources, credentials, agents, syncs, webhooks, listeners, virtual tables, and exports.
2. **Dataset Studio**: structured, semi-structured, unstructured, stream, and media resources with transaction history.
3. **Lineage**: data movement, transformations, validation, ontology mappings, schedules, and consumers.
4. **Data Health**: content validity, operational health, monitoring views, alert routing, and incident history.
5. **Ontology Manager**: object types, link types, object/link backing datasets, identity rules, and serving indexes.

Use a dark, dense, resource-oriented UI similar in spirit to Foundry: persistent left resource navigation, central graph/detail views, right-side configuration panels, tabs for Overview/Runs/Schema/Health/Lineage/Permissions, and React Flow-style lineage graphs. Use Blueprint.js or a similarly dense enterprise component system.

## North Star

The platform should treat connectors, syncs, datasets, health rules, object types, and links as durable resources rather than background jobs. Every operation produces lineage events, metrics, logs, and immutable transaction metadata.

Key principles:

- **Everything is a resource**: source, sync, dataset, stream, media set, schema, validation rule, monitoring view, object type, link type, agent, credential reference, and policy.
- **Data movement is transactional**: batch and incremental syncs commit dataset transactions; streaming syncs commit offsets and micro-batches; failed runs do not silently produce partial trusted data.
- **Validity and health are separate planes**: content validity asks whether data violates an expected contract; operational health asks whether a resource, pipeline, or observed value is abnormal.
- **Raw data is immutable**: raw landing data is never edited in place. Curated layers, object tables, and indexes are derived and rebuildable.
- **Object graph is backed by data**: object types and link types are semantic views over actual tables, files, streams, media, and identity rules.
- **Use code when point-and-click is insufficient**: no-code connectors cover common cases; generic REST, LDAP, RSS, GraphQL, JDBC, filesystem, and custom code connectors cover everything else.

## Overall Architecture

```mermaid
flowchart LR
    subgraph External["External Systems"]
        DB["Databases and Warehouses"]
        SaaS["SaaS APIs"]
        Files["File Stores"]
        Queues["Kafka Kinesis Pub/Sub"]
        DirectUpload["User Drag and Drop"]
        Legacy["LDAP RSS REST GraphQL OData"]
    end

    subgraph Access["Connection Access Layer"]
        SourceCatalog["Source Catalog"]
        CredentialVault["Credential Vault"]
        EgressPolicy["Egress Policy Engine"]
        AgentProxy["Edge Agent Proxy"]
        EdgeWorker["Edge Worker"]
        PlatformWorker["Platform Worker"]
    end

    subgraph Ingest["Ingestion and Transfer Plane"]
        Batch["Batch Sync Engine"]
        Incremental["Incremental Sync Engine"]
        Streaming["Streaming Sync Engine"]
        Listener["Inbound Listener Gateway"]
        Upload["Upload Service"]
        Virtualizer["Virtual Table and Media Registry"]
    end

    subgraph Storage["Storage Plane"]
        Raw["Raw Landing Object Store"]
        Lakehouse["Dataset Store Iceberg/Delta"]
        StreamStore["Stream Store Kafka/Redpanda"]
        Media["Media Sets and Blob Store"]
        Quarantine["Quarantine Store"]
        Catalog["Metadata Catalog"]
    end

    subgraph Semantics["Semantic and Serving Plane"]
        Transform["Transform Runtime"]
        Validity["Content Validity Engine"]
        Ontology["Ontology Registry"]
        ObjectStore["Object and Link Tables"]
        Search["Search Vector Graph Indexes"]
        API["Resource and Object APIs"]
    end

    subgraph Health["Operational Health Plane"]
        Metrics["Metrics"]
        Logs["Logs"]
        Traces["Traces"]
        HealthRules["Monitoring Views"]
        Alerts["Alert Router"]
    end

    subgraph UI["Palantir-Like UI"]
        DC["Data Connection"]
        DS["Dataset Studio"]
        LH["Lineage"]
        DH["Data Health"]
        OM["Ontology Manager"]
    end

    DB --> SourceCatalog
    SaaS --> SourceCatalog
    Files --> SourceCatalog
    Queues --> SourceCatalog
    Legacy --> SourceCatalog
    DirectUpload --> Upload

    SourceCatalog --> PlatformWorker
    SourceCatalog --> AgentProxy
    SourceCatalog --> EdgeWorker
    CredentialVault --> PlatformWorker
    CredentialVault --> EdgeWorker
    EgressPolicy --> PlatformWorker
    AgentProxy --> PlatformWorker

    PlatformWorker --> Batch
    PlatformWorker --> Incremental
    PlatformWorker --> Streaming
    EdgeWorker --> Batch
    EdgeWorker --> Incremental
    EdgeWorker --> Streaming
    AgentProxy --> PlatformWorker
    Listener --> Streaming
    Upload --> Raw

    Batch --> Raw
    Incremental --> Raw
    Streaming --> StreamStore
    Virtualizer --> Catalog

    Raw --> Lakehouse
    StreamStore --> Lakehouse
    Raw --> Media
    Lakehouse --> Transform
    Transform --> Validity
    Validity --> Lakehouse
    Validity --> Quarantine
    Lakehouse --> Ontology
    Media --> Ontology
    Ontology --> ObjectStore
    ObjectStore --> Search
    ObjectStore --> API

    Batch --> Metrics
    Incremental --> Metrics
    Streaming --> Metrics
    Transform --> Metrics
    Validity --> Metrics
    API --> Metrics
    Metrics --> HealthRules
    Logs --> HealthRules
    Traces --> HealthRules
    HealthRules --> Alerts

    DC --> SourceCatalog
    DS --> Lakehouse
    LH --> Catalog
    DH --> HealthRules
    OM --> Ontology
```

## Control Plane Vs Data Plane

```mermaid
flowchart TB
    subgraph Control["Control Plane: low volume, strongly consistent"]
        APIService["API Gateway"]
        Authz["AuthN/AuthZ"]
        ResourceRegistry["Resource Registry"]
        SyncRegistry["Sync Definitions"]
        SchemaRegistry["Schema Registry"]
        PolicyRegistry["Policy Registry"]
        RunLedger["Run and Transaction Ledger"]
        LineageCatalog["Lineage Catalog"]
        HealthConfig["Health Rule Config"]
        OntologyConfig["Ontology Config"]
        Postgres["Postgres Metadata DB"]
    end

    subgraph Data["Data Plane: high volume, elastic"]
        WorkerPool["Kubernetes Worker Pool"]
        Spark["Spark/Ray Batch Compute"]
        Flink["Flink Streaming Compute"]
        Trino["Trino Query Engine"]
        ObjectStore["S3/MinIO Object Storage"]
        Iceberg["Apache Iceberg Catalog"]
        Kafka["Kafka/Redpanda Streams"]
        VectorStore["pgvector/Milvus"]
        SearchStore["OpenSearch"]
    end

    subgraph HealthPlane["Health and Observability Plane"]
        OTel["OpenTelemetry Collectors"]
        Prom["Prometheus/Mimir Metrics"]
        Loki["Loki Logs"]
        Tempo["Tempo Traces"]
        Alertmanager["Alertmanager/PagerDuty/Slack/Webhook"]
    end

    APIService --> Authz
    APIService --> ResourceRegistry
    ResourceRegistry --> Postgres
    SyncRegistry --> Postgres
    SchemaRegistry --> Postgres
    PolicyRegistry --> Postgres
    RunLedger --> Postgres
    LineageCatalog --> Postgres
    HealthConfig --> Postgres
    OntologyConfig --> Postgres

    SyncRegistry --> WorkerPool
    WorkerPool --> Spark
    WorkerPool --> Flink
    Spark --> ObjectStore
    Flink --> Kafka
    Kafka --> ObjectStore
    ObjectStore --> Iceberg
    Iceberg --> Trino
    Iceberg --> VectorStore
    Iceberg --> SearchStore

    WorkerPool --> OTel
    Spark --> OTel
    Flink --> OTel
    Trino --> OTel
    OTel --> Prom
    OTel --> Loki
    OTel --> Tempo
    Prom --> Alertmanager
```

## Core Resource Model

```mermaid
classDiagram
    class Source {
        id
        connector_type
        worker_mode
        network_policy_refs
        credential_refs
        owner
    }

    class ConnectorDriver {
        name
        capabilities
        config_schema
        auth_methods
        runtime_contract
    }

    class SyncDefinition {
        id
        source_id
        mode
        destination
        cursor_policy
        schedule_or_trigger
        transaction_type
    }

    class SyncRun {
        id
        sync_id
        started_at
        completed_at
        status
        source_offsets
        committed_transaction_id
    }

    class Dataset {
        id
        data_kind
        path
        current_view
        schema_id
    }

    class DatasetTransaction {
        id
        dataset_id
        type
        state
        manifest_uri
        schema_id
    }

    class Stream {
        id
        topic
        schema_id
        partition_count
        retention_policy
    }

    class ValidityRule {
        id
        scope
        severity
        fail_policy
        expression
    }

    class ValidityIssue {
        id
        rule_id
        resource_id
        transaction_id
        row_or_file_ref
        status
    }

    class MonitoringRule {
        id
        scope
        metric
        threshold
        severity
    }

    class ObjectType {
        id
        api_name
        primary_key
        backing_dataset
        property_mapping
    }

    class LinkType {
        id
        api_name
        source_object_type
        target_object_type
        backing_dataset
        cardinality
    }

    Source --> ConnectorDriver
    SyncDefinition --> Source
    SyncRun --> SyncDefinition
    SyncRun --> DatasetTransaction
    DatasetTransaction --> Dataset
    Stream --> SyncDefinition
    ValidityRule --> Dataset
    ValidityIssue --> ValidityRule
    MonitoringRule --> Source
    MonitoringRule --> Dataset
    ObjectType --> Dataset
    LinkType --> ObjectType
```

## Connector Runtime Architecture

Mirror Foundry's worker/networking split, but rename it for this platform:

- **Platform worker**: default. Runs connector compute in your Kubernetes environment. Best for cloud/SaaS/public endpoints and private endpoints reachable through controlled egress.
- **Edge agent proxy**: preferred for private networks. Agent runs in the customer network and creates outbound tunnels; compute still runs on the platform worker.
- **Edge worker**: advanced. Agent runs compute close to the source for heavy file filtering, strict data-gravity constraints, or source systems that cannot tolerate remote reads. Use sparingly because it is harder to operate.
- **Direct upload worker**: browser/user upload path for ad hoc files. It creates a source and sync run automatically, so manual uploads still have lineage.

```mermaid
flowchart LR
    subgraph UserNetwork["Customer Private Network"]
        PrivateDB["Private DB"]
        PrivateFS["Private File Share"]
        EdgeProxy["Edge Agent Proxy"]
        EdgeCompute["Edge Worker"]
    end

    subgraph Platform["Platform Network"]
        UI["Data Connection UI"]
        Control["Control Plane"]
        Vault["Vault/KMS"]
        Egress["Egress Policy"]
        Workers["Platform Worker Pool"]
        Landing["Raw Landing Store"]
        Ledger["Run Ledger"]
    end

    subgraph Public["Public/Cloud Systems"]
        SaaS["SaaS API"]
        CloudDB["Cloud DB"]
        Bucket["Cloud Object Store"]
    end

    UI --> Control
    Control --> Vault
    Control --> Egress
    Control --> Workers
    Workers --> SaaS
    Workers --> CloudDB
    Workers --> Bucket
    Workers --> EdgeProxy
    EdgeProxy --> PrivateDB
    EdgeProxy --> PrivateFS
    EdgeCompute --> PrivateDB
    EdgeCompute --> PrivateFS
    EdgeCompute --> Landing
    Workers --> Landing
    Workers --> Ledger
    EdgeCompute --> Ledger
```

## Connector Driver Catalog

Target driver parity with the Palantir-documented connector families, implemented through open protocols, vendor SDKs, JDBC/ODBC drivers, or licensed third-party connectors. Do not assume Palantir proprietary driver binaries are reusable without a license.

| Family | Examples | Data kinds | Sync modes | Implementation |
| --- | --- | --- | --- | --- |
| SQL/JDBC | PostgreSQL, SQL Server, Oracle, MySQL, DB2, SAP HANA | Structured | Batch, incremental, CDC where supported | JDBC/ODBC, Debezium for CDC, source cursors |
| Warehouses | Snowflake, BigQuery, Redshift, Databricks | Structured | Batch, incremental, virtual tables, exports | Native SDK/JDBC, Iceberg/Delta interop |
| Object stores | S3, Azure Blob/ABFS, GCS, SMB, SFTP | Structured, semi-structured, unstructured | Batch, incremental, media sync | File listing, manifests, object checksums |
| Streaming | Kafka, Kinesis, Pub/Sub, Event Hubs | Semi-structured, binary, structured events | Streaming, streaming export | Kafka protocol, cloud SDKs, schema registry |
| SaaS | Salesforce, NetSuite, SAP, Workday-like, Jira, GitHub | Structured, semi-structured | Batch, incremental, webhooks | Vendor APIs, pagination, rate limit controls |
| Generic API | REST, GraphQL, OData | Semi-structured | Batch via code, webhooks, exports | HTTP client, OAuth2, pagination templates |
| Directory | LDAP, Azure AD, Google Directory | Structured, graph-like | Batch, incremental where supported | LDAP/client SDKs, identity deltas |
| Feeds | RSS, email, webhooks | Semi-structured, unstructured | Batch, listener, streaming | Feed polling, inbound listener gateway |
| Manual upload | CSV, XLSX, JSON, XML, PDF, images, video | All | One-shot batch, append upload | Browser multipart upload, schema inference |
| Virtualization | Snowflake, warehouses, object table formats | Structured, unstructured media | Virtual tables/media | Metadata registration without copying bytes |

## Sync Modes And Transfer Semantics

| Mode | Trigger | Source read behavior | Destination | Transaction/offset behavior | Best use |
| --- | --- | --- | --- | --- | --- |
| Batch snapshot | Schedule or manual run | Read complete selected source | Dataset | Commit `SNAPSHOT`; replace current view | Small/medium tables, stable exports, full refresh |
| Incremental append | Schedule, manual, or event | Read only new records/files by cursor, watermark, path, checksum, or offset | Dataset | Commit `APPEND`; downstream can process deltas | Large append-only sources, event logs, daily files |
| Incremental update/merge | Schedule, manual, CDC micro-batch | Read new and changed rows/files | Dataset/Iceberg table | Commit `UPDATE` or merge; downstream may require full recompute | Mutable source tables, corrections, late arriving changes |
| CDC streaming | Continuous | Read database change log | Stream plus lakehouse table | Persist source LSN/offset; compact by primary key if needed | Low latency DB replication |
| Streaming sync | Continuous | Consume queue/topic | Stream | Commit per offset range; checkpoint partitions | Kafka, Kinesis, Pub/Sub, sensors |
| Push ingestion | External system calls platform | Receive HTTP records | Stream or raw dataset | Validate request, write record batch, return receipt | Custom applications, IoT, systems that can call APIs |
| Listener ingestion | External webhook/email/websocket | Receive nonstandard inbound payload | Stream, media set, compute module | Verify signature/sender, write event, emit lineage | SaaS webhooks, inbound email, telephony |
| Virtual table/media | Query-time | Register external table/media metadata | Catalog resource | No byte copy; health tracks reachability and query latency | Data too large or governed to stay in source |
| Drag and drop | User action | Browser uploads files | Dataset or media set | Commit one upload transaction with manifest | Analyst uploads, ad hoc documents, prototyping |

## Batch And Incremental Transfer

```mermaid
sequenceDiagram
    participant User as User/UI
    participant Control as Control Plane
    participant Worker as Sync Worker
    participant Source as External Source
    participant Raw as Raw Landing Store
    participant Lake as Dataset Store
    participant Validity as Content Validity
    participant Health as Operational Health
    participant Ledger as Run Ledger

    User->>Control: Create or run sync
    Control->>Ledger: Open SyncRun
    Control->>Worker: Start run with source, cursor, policy
    Worker->>Source: Explore/read selected data
    Worker->>Raw: Write raw files and manifest
    Worker->>Lake: Open dataset transaction
    Worker->>Lake: Commit SNAPSHOT/APPEND/UPDATE
    Worker->>Ledger: Record transaction id and new cursor
    Worker->>Validity: Evaluate schema/content rules
    Validity-->>Lake: Mark trusted if pass
    Validity-->>Lake: Abort/block if fail-fast rule
    Validity-->>Health: Emit validity issue
    Worker->>Health: Emit status, duration, bytes, rows
    Health-->>User: Alert only if rule threshold fires
```

Important behavior:

- A failed batch or incremental sync aborts the dataset transaction and leaves the trusted view unchanged.
- Raw landing data can be retained for forensics even when trusted commit is blocked.
- Incremental APPEND is preferred for file feeds and event-like tables because it gives lower retry cost and end-to-end incremental processing.
- Incremental UPDATE/MERGE is allowed, but it must be marked as non-append-only so downstream pipelines know they may need snapshot recomputation.

## Streaming Transfer

```mermaid
sequenceDiagram
    participant Source as Queue/CDC Source
    participant StreamWorker as Streaming Worker
    participant Schema as Schema Registry
    participant Stream as Kafka/Redpanda Topic
    participant Validate as Streaming Validity
    participant DLQ as Quarantine/DLQ
    participant Lake as Stream Backing Table
    participant Ontology as Object Mapper
    participant Health as Operational Health

    StreamWorker->>Source: Subscribe with saved offsets
    loop Continuous
        Source-->>StreamWorker: Record batch
        StreamWorker->>Schema: Validate envelope/schema version
        StreamWorker->>Stream: Write canonical event
        StreamWorker->>Validate: Apply lightweight validity rules
        Validate-->>DLQ: Invalid events with reason
        Validate-->>Lake: Valid events to micro-batch table
        Lake-->>Ontology: Optional object/link upsert stream
        StreamWorker->>Health: Lag, throughput, errors, restarts
    end
```

Streaming design rules:

- Keep the original event payload and a canonical envelope: source id, sync id, partition, offset, ingest timestamp, event time, schema version, hash, and security markings.
- Validate cheap rules inline; run expensive semantic checks asynchronously.
- Never drop invalid events. Send them to a quarantine topic/table with the failure reason and replay instructions.
- Persist offsets only after writing records and validity outcomes.
- Support ordered keys for object updates and CDC compaction.

## Storage Architecture

```mermaid
flowchart TB
    subgraph Landing["Immutable Landing"]
        RawFiles["raw/{source}/{sync}/{run}/files"]
        RawEvents["raw/{source}/{sync}/{run}/events"]
        Manifests["raw/{source}/{sync}/{run}/manifest.json"]
    end

    subgraph Lakehouse["Lakehouse Datasets"]
        Bronze["bronze source-shaped tables"]
        Silver["silver conformed tables"]
        Gold["gold business datasets"]
        IcebergMeta["Iceberg/Delta metadata"]
    end

    subgraph Special["Specialized Stores"]
        Streams["Kafka/Redpanda topics"]
        StreamBacking["stream backing Iceberg tables"]
        MediaBlob["media blobs, thumbnails, OCR"]
        Vectors["embeddings and chunks"]
        GraphIndex["object/link graph index"]
        SearchIndex["OpenSearch full text index"]
    end

    subgraph Metadata["Metadata Stores"]
        Catalog["resource catalog"]
        Schemas["schemas and contracts"]
        Runs["runs and transactions"]
        Lineage["lineage events"]
        Health["validity and health findings"]
    end

    RawFiles --> Bronze
    RawEvents --> Streams
    Streams --> StreamBacking
    Bronze --> Silver
    Silver --> Gold
    Bronze --> MediaBlob
    MediaBlob --> Vectors
    Silver --> GraphIndex
    Gold --> GraphIndex
    Silver --> SearchIndex
    Gold --> SearchIndex
    IcebergMeta --> Catalog
    Manifests --> Runs
    Schemas --> Catalog
    Lineage --> Catalog
    Health --> Catalog
```

Physical storage map:

| Store | Technology | Contains | Retention |
| --- | --- | --- | --- |
| Metadata DB | PostgreSQL | resources, sync specs, schedules, policy refs, schema refs, health rule configs | Long-lived, backed up |
| Secret store | Vault or cloud KMS/Secrets Manager | encrypted credentials and tokens | Rotated, never copied into logs |
| Raw landing | S3/MinIO/GCS/Azure Blob | immutable source files, event batches, manifests | Policy-based, usually long enough for replay |
| Dataset store | Apache Iceberg or Delta on object storage | structured/semi-structured tables and dataset transactions | Governed by dataset retention |
| Stream store | Kafka/Redpanda/Pulsar | low-latency records, CDC, listener events | Short to medium retention plus lakehouse backing |
| Media store | Object storage plus metadata tables | PDFs, images, video, audio, thumbnails, OCR text, extracted metadata | Usually long-lived |
| Quarantine store | Iceberg tables plus object storage plus DLQ topics | invalid rows/files/events and reasons | Long enough for remediation/replay |
| Search index | OpenSearch | resource search, text search, logs search | Rebuildable from source data |
| Vector index | pgvector or Milvus | document chunks, embeddings, semantic search | Rebuildable from media/text extraction |
| Graph/object index | Neo4j, JanusGraph, or service-owned indexes over Iceberg | object and link traversal acceleration | Rebuildable from object/link tables |
| Metrics store | Prometheus/Mimir | counters, gauges, histograms | 30-180 days hot, archive optional |
| Logs/traces | Loki and Tempo | logs, spans, traces | Operational retention by severity |

## Data Kind Handling

```mermaid
flowchart LR
    Upload["Upload or Sync"] --> Detect["Kind Detection"]
    Detect --> Structured["Structured"]
    Detect --> Semi["Semi-Structured"]
    Detect --> Unstructured["Unstructured"]

    Structured --> SchemaInfer["Schema Infer/Import"]
    SchemaInfer --> TableDataset["Tabular Dataset"]
    TableDataset --> SQL["SQL/Transform"]
    SQL --> ObjectMap["Object Mapping"]

    Semi --> RawJsonXml["Raw JSON/XML/Avro/Logs"]
    RawJsonXml --> Parser["Parser Transform"]
    Parser --> TableDataset
    Parser --> Quarantine["Parse Quarantine"]

    Unstructured --> MediaSet["Media Set"]
    MediaSet --> Extract["OCR/Text/Metadata/Chunking"]
    Extract --> TextTables["Extracted Text Tables"]
    Extract --> Embeddings["Vector Embeddings"]
    TextTables --> ObjectMap
    Embeddings --> Search["Semantic Search"]
```

| Data kind | Landing format | Trusted representation | Typical validity checks | Notes |
| --- | --- | --- | --- | --- |
| Structured | Parquet/Avro/CSV snapshots or row batches | Iceberg table with schema | schema, column type, primary key, null percent, allowed values, ranges | Best for SQL, BI, object backing datasets |
| Semi-structured | raw JSON/XML/Avro/text logs | raw dataset plus parsed table | parse success, schema evolution, required fields, event time, nested field rules | Preserve raw payload for replay and schema reparse |
| Unstructured | PDF/image/video/audio/binary files | media set plus extracted metadata/text/chunks | file type, size, checksum, OCR success, required metadata, content classification | Media bytes stay in blob store; derived text/tables power search and ontology |
| Streaming | canonical event envelope plus payload | stream topic plus backing table | envelope schema, key, event time, JSON schema, CDC operation | DLQ/quarantine must be replayable |
| Virtual | external metadata only | virtual table/media resource | reachability, schema drift, permission test, query latency | Does not copy data; still emits health and lineage |

## Dataset Transaction Semantics

Borrow the strongest part of Foundry's dataset model: dataset views are transaction-backed.

```mermaid
stateDiagram-v2
    [*] --> Open: create transaction
    Open --> Committed: commit files and manifest
    Open --> Aborted: validation fail or run fail
    Committed --> CurrentView: if latest accepted transaction
    Committed --> HistoricalView: superseded by later transaction
    Aborted --> [*]
```

Transaction types:

| Transaction | Meaning | Downstream implication |
| --- | --- | --- |
| `SNAPSHOT` | Replace current view with a new complete set of files | Simple, reliable, more expensive for large data |
| `APPEND` | Add new files/records without changing previous files | Enables true incremental downstream processing |
| `UPDATE` | Add or replace existing files/rows | Needed for mutable sources, weakens incremental guarantees |
| `DELETE` | Remove file/row references from the current view | Used for retention, legal deletion, and corrected datasets |

## Content Validity Vs Operational Health

This split is mandatory. Do not overload one concept with the other.

```mermaid
flowchart TB
    ResourceEvent["Dataset/stream/sync/object event"] --> Classifier["Health Classifier"]

    Classifier --> Validity["Content Validity Plane"]
    Classifier --> Operational["Operational Health Plane"]

    Validity --> Contracts["Contracts and Expectations"]
    Validity --> SchemaChecks["Schema Checks"]
    Validity --> SemanticChecks["Semantic Checks"]
    Validity --> ReferentialChecks["Object/Link Checks"]
    Validity --> ValidityIssues["Validity Issues"]
    ValidityIssues --> Block["Block/Abort"]
    ValidityIssues --> Quarantine["Quarantine"]
    ValidityIssues --> Warn["Warn and Commit"]

    Operational --> ResourceMetrics["Resource Metrics"]
    Operational --> RuntimeSignals["Logs Traces Errors"]
    Operational --> AnomalyDetection["Anomaly Detection"]
    Operational --> SLOs["SLOs and Freshness"]
    Operational --> HealthAlerts["Health Alerts"]
    HealthAlerts --> Incident["Incident Workflow"]
```

### Content Validity

Content validity means data violates an expected data contract. The data may have arrived successfully, but the content is not acceptable for trusted use.

Examples:

- Missing required column.
- Column type changed from integer to string.
- Primary key is null or duplicated.
- `country_code` not in allowed values.
- Email, identifier, timestamp, or file name fails regex.
- Numeric value outside an agreed domain range.
- JSON/XML cannot be parsed into the expected schema.
- Object primary key is unstable across builds.
- Link points to a non-existent object.
- Required document metadata is missing.
- PDF/image/video cannot be decoded or OCR extraction fails.

Validity actions:

| Severity | Action | Storage outcome |
| --- | --- | --- |
| Info | Commit and record issue | Dataset trusted; issue visible in health |
| Warning | Commit with warning | Dataset trusted but yellow health |
| Error | Commit to untrusted/quarantine branch | Data available for remediation, not default trusted view |
| Critical | Abort transaction or stop stream promotion | Trusted view unchanged; invalid payload in quarantine |

### Operational Health

Operational health means the data may be real, but the system behavior, resource state, or observed metric is abnormal.

Examples:

- Sync failed, timed out, retried too often, or exceeded duration threshold.
- Streaming consumer lag is growing.
- Agent is offline or restarting.
- Source credentials expired.
- Row count dropped 80 percent compared with historical median.
- Data freshness exceeds SLO.
- Dataset file count exploded, causing poor partition health.
- API rate limits throttle syncs.
- Worker CPU/memory is saturated.
- Object API P95 latency crosses threshold.
- Log error rate spikes.

Operational actions:

| Signal | Typical action |
| --- | --- |
| Freshness violation | Alert owner; annotate lineage; keep prior data serving |
| Duration anomaly | Alert pipeline owner; inspect skew, source latency, or code change |
| Volume anomaly | Alert as operational anomaly first; only validity issue if a contract says volume range is invalid |
| Agent/source unavailable | Page connector owner; pause dependent schedules if needed |
| Stream lag | Scale consumers, check source partitions, preserve offset checkpoints |
| Resource saturation | Autoscale or move workload class |

## Data Health Architecture

```mermaid
flowchart LR
    subgraph Inputs["Health Inputs"]
        RunEvents["Run events"]
        DatasetTx["Dataset transactions"]
        StreamOffsets["Stream offsets"]
        ValidationResults["Validation results"]
        ResourceMetrics["Resource metrics"]
        Logs["Logs"]
        Traces["Traces"]
    end

    subgraph HealthCore["Health Core"]
        RuleEngine["Rule Engine"]
        AnomalyEngine["Anomaly Engine"]
        ScopeResolver["Dynamic Scope Resolver"]
        StateStore["Health State Store"]
        History["Health History"]
    end

    subgraph UX["Data Health UI"]
        ResourceHealth["Resource Health Page"]
        MonitoringViews["Monitoring Views"]
        AlertDebug["Alert Debug Page"]
        LineageOverlay["Lineage Health Overlay"]
    end

    subgraph Outputs["Outputs"]
        Notifications["In-App and Email"]
        PagerDuty["PagerDuty"]
        Slack["Slack"]
        Webhook["Webhook"]
        Issue["Issue/Ticket"]
    end

    RunEvents --> RuleEngine
    DatasetTx --> RuleEngine
    StreamOffsets --> RuleEngine
    ValidationResults --> RuleEngine
    ResourceMetrics --> AnomalyEngine
    Logs --> AnomalyEngine
    Traces --> AnomalyEngine
    ScopeResolver --> RuleEngine
    RuleEngine --> StateStore
    AnomalyEngine --> StateStore
    StateStore --> History
    StateStore --> ResourceHealth
    StateStore --> MonitoringViews
    StateStore --> AlertDebug
    StateStore --> LineageOverlay
    StateStore --> Notifications
    StateStore --> PagerDuty
    StateStore --> Slack
    StateStore --> Webhook
    StateStore --> Issue
```

Mandatory health rule families:

| Family | Validity or operational | Example rules |
| --- | --- | --- |
| Status | Operational | sync status, build status, schedule status, job status |
| Time | Operational | time since last update, sync freshness, data freshness, sync duration, build duration |
| Size | Usually operational | row count, file count, file size, transaction size, partition health |
| Schema | Content validity | schema exact match, additions allowed, required columns, column count, column types |
| Content | Content validity | allowed values, regex, primary key, null percentage, numeric range, date range |
| Referential | Content validity | object key stability, link target exists, cardinality, duplicate links |
| Resource | Operational | agent heartbeat, worker saturation, stream lag, API error rate, credential expiry |
| Security/governance | Both | policy violation is validity for trusted data; permission drift is operational/security health |

## Ontology And Object Graph

Objects and links should be generated from backing datasets, not hand-entered into an abstract graph.

```mermaid
flowchart LR
    subgraph DataAssets["Backed Data Assets"]
        EmployeeTable["employee table"]
        CompanyTable["company table"]
        EmploymentTable["employment link table"]
        Documents["contracts media set"]
    end

    subgraph OntologyConfig["Ontology Config"]
        EmployeeType["ObjectType Employee"]
        CompanyType["ObjectType Company"]
        ContractType["ObjectType Contract"]
        WorksFor["LinkType Employee works_for Company"]
        SignedBy["LinkType Contract signed_by Company"]
        Identity["Identity and Primary Key Rules"]
    end

    subgraph Build["Object Build"]
        ObjectBuilder["Object Builder"]
        LinkBuilder["Link Builder"]
        Validity["Referential Validity"]
    end

    subgraph Serving["Serving Layer"]
        ObjectTables["Object Tables"]
        LinkTables["Link Tables"]
        ObjectAPI["Object API"]
        GraphIndex["Graph/Search Index"]
        Apps["Applications and Analytics"]
    end

    EmployeeTable --> EmployeeType
    CompanyTable --> CompanyType
    Documents --> ContractType
    EmploymentTable --> WorksFor
    Documents --> SignedBy
    EmployeeType --> Identity
    CompanyType --> Identity
    ContractType --> Identity
    Identity --> ObjectBuilder
    WorksFor --> LinkBuilder
    SignedBy --> LinkBuilder
    ObjectBuilder --> Validity
    LinkBuilder --> Validity
    Validity --> ObjectTables
    Validity --> LinkTables
    ObjectTables --> ObjectAPI
    LinkTables --> ObjectAPI
    ObjectTables --> GraphIndex
    LinkTables --> GraphIndex
    ObjectAPI --> Apps
    GraphIndex --> Apps
```

Object storage model:

| Asset | Physical representation | Required metadata |
| --- | --- | --- |
| Object type | table or materialized view over one or more datasets | API name, display name, primary key, property mapping, security policy, source lineage |
| Object instance | row keyed by stable primary key | object id, properties, transaction version, provenance |
| Link type | join/link table between object primary keys | source object type, target object type, cardinality, directionality, backing dataset |
| Link instance | row keyed by source id, target id, link type, optional effective time | provenance, confidence, validity state |
| Object set | saved filter over object type or graph traversal | predicate, permissions, version |
| Derived property | computed property over object/link data | expression, dependencies, refresh policy |

Referential validity rules:

- Object primary keys must be unique, non-null, and stable.
- Many-to-one and one-to-one links must respect cardinality.
- Link rows must resolve both endpoints unless configured as soft links.
- Link tables need effective time if relationships are temporal.
- Object/link build outputs must store source row/file references for traceability.

## Lineage And Data Transfer Trace

```mermaid
flowchart LR
    Source["Source"] --> Sync["Sync Definition"]
    Sync --> Run["Sync Run"]
    Run --> Raw["Raw Manifest"]
    Raw --> Tx["Dataset Transaction"]
    Tx --> Dataset["Dataset View"]
    Dataset --> Transform["Transform"]
    Transform --> Curated["Curated Dataset"]
    Curated --> Validity["Validity Check Result"]
    Curated --> ObjectType["Object Type"]
    ObjectType --> LinkType["Link Type"]
    ObjectType --> App["Application/API"]
    LinkType --> App

    Run -.metrics.-> Health["Operational Health"]
    Validity -.issues.-> Health
    Health -.alerts.-> Owner["Owner/On-call"]
```

Every node and edge should be queryable. A user should be able to start from an alert and navigate to:

- failing rule,
- affected resource,
- source connector,
- last successful transaction,
- exact files/rows/events affected,
- downstream datasets,
- object types and links impacted,
- applications consuming those objects.

## UI Information Architecture

```mermaid
flowchart TB
    Shell["Platform Shell"]
    Shell --> Compass["Resource Explorer"]
    Shell --> DataConnection["Data Connection"]
    Shell --> DatasetStudio["Dataset Studio"]
    Shell --> Lineage["Lineage"]
    Shell --> DataHealth["Data Health"]
    Shell --> OntologyManager["Ontology Manager"]
    Shell --> Admin["Admin and Policy"]

    DataConnection --> Sources["Sources"]
    DataConnection --> Syncs["Syncs"]
    DataConnection --> Agents["Agents"]
    DataConnection --> Webhooks["Webhooks"]
    DataConnection --> Listeners["Listeners"]

    DatasetStudio --> Preview["Preview"]
    DatasetStudio --> Schema["Schema"]
    DatasetStudio --> History["Transactions"]
    DatasetStudio --> Files["Files/Media"]
    DatasetStudio --> HealthTab["Health"]

    DataHealth --> Monitoring["Monitoring Views"]
    DataHealth --> ValidityIssues["Validity Issues"]
    DataHealth --> OpsAlerts["Operational Alerts"]
    DataHealth --> AlertDebug["Alert Debug"]

    OntologyManager --> Objects["Object Types"]
    OntologyManager --> Links["Link Types"]
    OntologyManager --> Mappings["Backing Data Mappings"]
    OntologyManager --> ObjectHealth["Object/Link Health"]
```

Key UI tabs per resource:

| Resource | Tabs |
| --- | --- |
| Source | Overview, Config, Credentials, Network, Capabilities, Syncs, Health, Permissions |
| Sync | Overview, Runs, Config, Cursor/Offsets, Destination, Health, Lineage |
| Dataset | Preview, Schema, Files, Transactions, Health, Lineage, Permissions |
| Stream | Preview, Schema, Partitions, Offsets, Consumers, Health, Lineage |
| Media set | Files, Preview, Extraction, Chunks/Embeddings, Health, Lineage |
| Object type | Overview, Properties, Backing data, Actions, Links, Health, Permissions |
| Link type | Overview, Endpoints, Cardinality, Backing data, Health, Permissions |
| Monitoring view | Overview, Rules, Alerts, Subscriptions, Debug, History |

## Required Technologies

Recommended default stack:

| Layer | Technology | Why |
| --- | --- | --- |
| UI | React, TypeScript, Blueprint.js, React Flow, Monaco | Dense Palantir-like enterprise UI, graph views, config editors |
| API | Go or Kotlin services, REST/gRPC, GraphQL for resource graph | Strong typed services, high concurrency, stable contracts |
| AuthN | OIDC/SAML, service accounts, OAuth2 client credentials | Enterprise identity and source push ingestion |
| AuthZ | OpenFGA or OPA plus resource ACLs | Fine-grained resource and lineage permissions |
| Control metadata | PostgreSQL | Strong consistency for resources, configs, runs, transactions |
| Secrets | Vault or cloud KMS/Secrets Manager | Encrypted source credentials and rotation |
| Orchestration | Temporal | Reliable sync workflows, retries, heartbeats, long-running operations |
| Compute scheduling | Kubernetes, Karpenter/Cluster Autoscaler | Isolated elastic workers |
| Batch compute | Spark plus Ray or DuckDB for smaller jobs | Large transforms and fast previews/profiling |
| Streaming compute | Flink or Kafka Streams | Stateful streaming, CDC, windowing, exactly-once-style sinks |
| Stream broker | Kafka, Redpanda, or Pulsar | Durable event ingestion, offsets, replay |
| Lakehouse | S3/MinIO plus Apache Iceberg | Open table format, transactions, schema evolution, time travel |
| SQL query | Trino | Interactive SQL over lakehouse and federated sources |
| Data quality | Great Expectations, Soda, Deequ, plus custom rules | Schema/content checks and data expectations |
| CDC | Debezium where available | Database changelog capture |
| Observability | OpenTelemetry, Prometheus/Mimir, Loki, Tempo | Metrics, logs, traces, resource health |
| Alerts | Alertmanager, PagerDuty, Slack, generic webhooks | External operational response |
| Search | OpenSearch | Resource, log, and document search |
| Vector | pgvector initially, Milvus at scale | Embeddings over documents/media/text |
| Graph serving | Service-owned indexes over Iceberg; Neo4j/JanusGraph if traversal becomes dominant | Object/link traversal without making graph DB the system of record |
| Data catalog | OpenMetadata/DataHub-compatible model or custom catalog | Discovery, ownership, lineage, glossary |
| Policy/audit | OPA, immutable audit log, object store WORM for high assurance | Governance and investigation |

## Ambitious Architectural Bets

1. **Unify batch and streaming around a sync ledger**  
   Even batch runs emit canonical ingest events. This allows replay, lineage, and health to work the same way across sync modes.

2. **Make validity issues queryable data**  
   Store validity issues as first-class tables, not just alerts. Users can join validity issues back to files, rows, objects, links, and source runs.

3. **Quarantine is a product surface, not a DLQ afterthought**  
   Quarantine has preview, owner assignment, replay, rule override, and diff tools.

4. **Virtualize before copying**  
   Support virtual tables/media for expensive or governed systems, then promote to copied datasets when latency, cost, or lineage requires it.

5. **Object graph is rebuildable**  
   Object and link serving indexes are derived from object/link tables. This avoids graph database lock-in and keeps lineage/audit strong.

6. **AI assists but never owns governance**  
   Use AI to propose schemas, object mappings, validation rules, and anomaly explanations. Require human approval and versioned rule changes.

7. **Agents are zero-trust resources**  
   Edge agents receive short-lived work leases, are scoped to source policies, and cannot exfiltrate arbitrary data.

## Minimal Build Sequence

```mermaid
flowchart LR
    P1["Phase 1: Resource Graph and Batch Ingest"] --> P2["Phase 2: Health and Lineage"]
    P2 --> P3["Phase 3: Incremental and Streaming"]
    P3 --> P4["Phase 4: Ontology Object/Link Serving"]
    P4 --> P5["Phase 5: Virtualization, Media, AI Assistance"]
```

Phase details:

| Phase | Deliver |
| --- | --- |
| 1 | source catalog, credentials, platform worker, direct/agent proxy networking, file/JDBC/REST connectors, raw landing, Iceberg datasets, upload connector |
| 2 | run ledger, transaction history, health checks, monitoring views, alert routing, lineage graph |
| 3 | incremental cursors, file APPEND mode, CDC, Kafka/Redpanda streams, listener gateway, quarantine |
| 4 | ontology registry, object type mapping, link type mapping, object/link validity, object API, graph/search indexes |
| 5 | virtual tables/media, media sets, OCR/chunking/embeddings, AI schema/rule/mapping suggestions, marketplace connector packages |

## Non-Negotiable Engineering Requirements

- Source credentials must be encrypted, scoped, rotated, and never emitted in logs.
- Network egress must be explicit per source and policy-reviewed.
- Every sync run must have a stable run id, manifest, status, metrics, and source cursor/offset record.
- Every dataset commit must be atomic from the user's trusted view.
- Every data asset must have owner, permissions, lineage, schema or declared schemaless state, and retention policy.
- Every validity rule must have owner, severity, action, scope, version, and historical result store.
- Every operational monitor must have scope, threshold or anomaly model, severity, subscription, and snooze/escalation behavior.
- Object and link types must declare stable identity rules before they can serve applications.
- Quarantine must be replayable.
- Observability must cover workers, agents, sources, syncs, datasets, streams, object APIs, and UI actions.

## Recommended Naming

To keep the system familiar without copying product names:

| Palantir-like concept | This system name |
| --- | --- |
| Data Connection | Connect |
| Source | Source |
| Foundry worker | Platform worker |
| Agent proxy | Edge agent proxy |
| Agent worker | Edge worker |
| Dataset | Dataset |
| Stream | Stream |
| Media set | Media set |
| Data Health | Health |
| Monitoring view | Monitoring view |
| Health check | Validity check or health monitor, depending on purpose |
| Ontology Manager | Object Model Manager |
| Object type | Object type |
| Link type | Link type |
| Data Lineage | Lineage |

