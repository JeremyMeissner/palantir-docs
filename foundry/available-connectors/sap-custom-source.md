---
source_url: "https://www.palantir.com/docs/foundry/available-connectors/sap-custom-source/"
title: "Documentation | SAP > SAP (Custom source)"
---
# SAP (Custom source)

The SAP (Custom source) connector allows you to connect Foundry to SAP systems using a manually configured source with the `magritte-sap-source` connector type. This connector uses a custom YAML-based setup rather than the guided configuration available in newer SAP connectors.

:::callout{theme="warning"}
New SAP integrations should use the [SAP ERP](/docs/foundry/available-connectors/sap-erp/) or [SAP SLT](/docs/foundry/available-connectors/sap-slt/) connectors. These connectors use a newer, more performant API to read data from SAP and provide a guided setup experience. The SAP (Custom source) connector is intended for existing integrations set up before those connector types were available.

Using the SAP (Custom source) connector requires the installation of the [Palantir Foundry Connector 2.0 for SAP Applications add-on](/docs/foundry/sap/overview/) on the target SAP application layer.
:::

## Supported capabilities

| Capability | Status |
|------------|--------|
| Exploration | 🟢 Generally available |
| Batch syncs | 🟢 Generally available |
| Incremental | 🟢 Generally available |
| Streaming syncs | 🟡 Beta |
| Webhooks | 🟢 Generally available |

## Setup

1. Open the [Data Connection](/docs/foundry/data-connection/overview/) application and select **+ New Source** in the upper right corner of the screen.

2. Select **Add Custom Source**.

3. Give the source a name and location.

4. In the custom YAML section, enter the source definition:

   ```yaml
   type: magritte-sap-source
   url: https://<host>:<port>/sap/palantir
   usernamePassword: <username>:{{password}}
   ```

   * `<host>` is the hostname of the SAP application server.
   * `<port>` is the HTTPS (or HTTP) port for the Internet Communication Manager (ICM).
   * The username and password are those of the technical user created for Foundry when installing the [Connector](/docs/foundry/sap/install-sap-connector/).

   :::callout{theme="warning"}
   Enter `{{password}}` exactly as shown. After saving, enter the password value under **Encrypted values** on the right side of the dialog.
   :::

5. Select **Save**.

Learn more about [setting up a connector](/docs/foundry/data-connection/set-up-source/) in Foundry.

### Enable streaming syncs (SLT only)

To support streaming syncs, the source must be configured with an explicit SLT connection type. Add the `connectionType` parameter to the source YAML:

```yaml
type: magritte-sap-source
url: https://<host>:<port>/sap/palantir
usernamePassword: <username>:{{password}}
connectionType:
  type: slt
  slt:
    context: <context>
```

The `context` value is the unique identifier of the RFC connection between the SLT Replication Server and the source ERP system. Learn more about [configuring SLT](/docs/foundry/sap/configure-sap-slt/#slt-configuration).

## Source configuration

The following parameters can be configured on the source.

| Parameter | Required | Default | Description |
|-----------|:--------:|:-------:|-------------|
| `url` | Yes | | Base URL of the SAP add-on service endpoint. |
| `usernamePassword` | Yes | | Username and password of the technical user created for Foundry. |
| `useKernelJsonSerialization` | No | `false` | Use kernel JSON serialization for paginated data. Incompatible with `useTsvFormat: true`. |
| `useTsvFormat` | No | `false` | Use TSV format for paginated data instead of JSON. |
| `output` | No | 50,000 rows | Maximum Parquet file size (rows or bytes) per request. Can also be [overridden per sync](#advanced-yaml-parameters). |
| `convertDatesToStrings` | No | `false` | Ingest all dates as strings for all syncs under this source. |
| `proxy` | No | None | Proxy configuration for connecting to SAP. |
| `cacheConfigurations` | No | None | Cache timeout configuration per SAP object type. |

## Networking and connectivity

Make sure to properly configure [egress policies](/docs/foundry/data-connection/set-up-source/#configure-network-access) to allow Foundry to reach the SAP system. For on-premises SAP environments, [agent proxy policies](/docs/foundry/data-connection/agent-proxy/) are typically required to route traffic correctly.

Many SAP systems use custom-signed certificates, which can cause SSL handshake exceptions when configuring the connection for the first time. Make sure you have the correct custom certificates from your system and [add them to the source](/docs/foundry/data-connection/set-up-source/#optional-add-certificates).

## Source exploration

Once the source has been created, use the SAP Source Explorer for interactive exploration.

1. Navigate to the source and select **Explore and create syncs**.
2. For remote and SLT connections, select the appropriate context.
3. Select the tables or modules of interest and add them to the graph.
## Batch syncs

### Create a sync

Create a sync for each SAP object you want to extract to Foundry.

:::callout{theme="neutral"}
The sync configuration UI has two modes: **Basic** and **Advanced**. The **Advanced** tab exposes the full sync definition as YAML and is required for some object types and configuration parameters documented below. You can switch back to the Basic view, but any YAML properties that have no UI equivalent will not be displayed and will be lost.
:::

1. From the source overview page, select **+ New** next to batch sync.
2. Configure the standard settings: name, target dataset, and schedule.
3. Set **Transaction type** to one of the following options:
   * **APPEND** — for incremental updates. See [Incremental syncs](#incremental-syncs) for details.
   * **SNAPSHOT** — for a full load.
4. Select an **SAP object type** (see [SAP object types](#sap-object-types) below).
5. If using SLT or connecting to a remote system, select a **Context**. See [Install a remote agent](/docs/foundry/sap/install-sap-remote-agent/) for details on contexts.
6. Enter the **Object name**. As you type, the field suggests matching objects based on the selected SAP object type.
7. If configuring an incremental sync, provide an **Incremental field**.
8. Optionally, configure additional parameters in the **Extras** tab.
### SAP object types

The following object types are available from the **SAP object type** dropdown in the sync configuration UI.

| Object type | Description |
|-------------|-------------|
| **ERP Table** | Extracts data from any ERP table or view in the SAP ABAP data dictionary, including custom Z\* tables. |
| **BW InfoProvider** | Extracts data from a BW InfoProvider (InfoCube, DataStore object, or MultiProvider). All SAP BW authorization concepts are inherited. |
| **BW BEx Query** | Runs a BEx query in a BW system. See [BEx query configuration](#bex-query-configuration) below. |
| **SLT** | Extracts data from an SLT Operational Delta Queue (ODQ). SLT is a trigger-based replication tool with a built-in CDC mechanism. Requires a **Context**. |
| **BW Content Extractor** | Runs an ERP Business Content extractor — ready-to-use structures with built-in business logic and CDC mechanisms. Use `APPEND` for extractors that support delta extraction. See [Configure extractors](/docs/foundry/sap/configure-extractors/). |
| **Function** | Runs a remote-enabled function or BAPI in an ERP or BW system. See [Function configuration](#function-configuration) below. |
| **ERP Table Data Model** | Reads the relationships between ERP tables based on a primary key/foreign key model. Use the `depth` parameter to control how many levels of relationships to follow. |
| **Remote ERP Table** | Extracts data from an ERP table in a remote ERP system. Requires a **Context** to identify the remote system. |
| **Remote BW InfoProvider** | Extracts data from a BW InfoProvider in a remote BW system. Requires a **Context**. |
| **Remote BW BEx Query** | Runs a BEx query in a remote BW system. Requires a **Context**. |
| **Remote Function** | Runs a remote-enabled function in a remote ERP or BW system. Requires a **Context**. |
| [**Transaction codes**](#transaction-codes) | Extracts data from SAP reports using ABAP List Viewer (ALV). Advanced tab only. |
| [**HANA views**](#hana-views) | Extracts data from HANA Views enabled in the SAP application layer. Advanced tab only. |
| [**CDS views**](#cds-views) | Extracts data from ABAP CDS (Core Data Services) Views. Advanced tab only. |

Remote object types require a **Context** value that identifies the remote system. Learn more about [remote connections](/docs/foundry/sap/architecture/#connecting-to-a-remote-sap-erp-system-via-a-gateway).

#### BEx query configuration

BEx is a multidimensional query framework built on SAP BW InfoProviders. BEx queries use standard SAP BW access methods and inherit all SAP BW authorization concepts. They represent business logic applied to InfoProvider views.

:::callout{theme="neutral"}
If the BEx query has dynamic columns (a characteristic on columns with key figures such that every key figure is repeated along with the characteristic value), this creates a dynamic output. Dynamic columns are not supported by Foundry — adjust your query accordingly.
:::

When you select **BW BEx Query** as the object type, the sync editor shows a dedicated BEx query builder with the following options:

| Option | Description |
|--------|-------------|
| **Use Technical Names** | Toggles between technical and human-readable (language-dependent) column names. |
| **Drop columns** | Removes key characteristics from the output. |
| **Free characteristics** | Adds free characteristics (as defined in the BEx query) to the output. |
| **Filter** | Filters data after the query is run (post-query filter). |
| **BEx Query Input Variables** | Provides filter values for BEx query input variables. |

For BEx paging configuration, see [Advanced YAML parameters](#advanced-yaml-parameters) in the sync parameters section.

#### Function configuration

SAP function modules can both extract data from and write data back to an SAP system. The Connector can only extract data from functions that have at least one tabular output parameter.

:::callout{theme="neutral"}
The Foundry technical user requires the following authorization roles to extract function results:

* `/PALANTIR/SERVICE_USER`
* `/PALANTIR/CONTENT_FUNCTION_ALL`
* Any authorization role or object required to run the specific function
:::

If a function returns more than one output parameter, use the `paramName` parameter to specify which output to write to the Foundry dataset:

```yaml
type: magritte-sap-source-adapter
sapType: function
obj: BAPI_USER_GETLIST
paramName: USERLIST
```

Input parameters can be configured using `inputParams`. Three value types are supported:

| Type | YAML syntax |
|------|-------------|
| Single value | `PARAM_NAME: 'value'` |
| Structure (dictionary) | `PARAM_NAME: '{"FIELD1": "value1", "FIELD2": "value2"}'` |
| Table (list of dictionaries) | `PARAM_NAME: '[{"FIELD1": "value1"}, {"FIELD1": "value2"}]'` |

Example with a table-type input parameter:

```yaml
type: magritte-sap-source-adapter
sapType: function
obj: EM_GET_NUMBER_OF_ENTRIES
inputParams:
  IT_TABLES: '[{"TABNAME":"TSTC"}]'
paramName: IT_TABLES
```

#### Advanced-only object types

The following object types are not available from the dropdown and must be configured from the **Advanced** tab.

##### Transaction codes

Extracts data generated by SAP reports. Only reports using ABAP List Viewer (ALV) are supported.

By transaction code name:

```yaml
type: magritte-sap-source-adapter
sapType: tcode
obj: ZTEST_ALV
```

By program name:

```yaml
type: magritte-sap-source-adapter
sapType: tcode
obj: RSUSR200
programType: program
```

The following optional parameters can be added to the sync YAML:

| Parameter | Description |
|-----------|-------------|
| `filter` | Passes user inputs for selection screen variables. Does not filter output fields arbitrarily. |
| `selectionVariant` | Passes a predefined selection screen variant. If combined with `filter`, the `filter` values overwrite matching variant values. |
| `outputVariant` | Passes the layout name of the program. Only supported for programs with a layout parameter defined on SAP's selection screen. |
| `ingestionType: spool` | Sends the report output to a printer queue before ingesting. Recommended for large reports that exceed SAP's internal table limits. When set, all columns are ingested as type `String`. |

##### HANA views

Extracts data from HANA Views enabled in the SAP application layer. See [Ingest HANA views from SAP](/docs/foundry/sap/ingest-hana-views/) for prerequisites.

```yaml
type: magritte-sap-source-adapter
sapType: hanaview
obj: ZEXT_SBOOK
```

##### CDS views

Extracts data from ABAP CDS (Core Data Services) Views. ABAP CDS defines semantic data models on the central database of the application server.

:::callout{theme="neutral"}
Extracting data from parametrized CDS views is not currently supported.
:::

### Incremental syncs

Incremental syncs are stateful syncs that enable append-style transactions from the same table. To enable incremental syncs, set **Transaction type** to **APPEND**.

The following incremental types are available:

| Incremental type | Description |
|-----------------|-------------|
| **Single field** | Imports rows where a single field is greater than or equal to the largest value already imported. |
| **Multiple fields** | Same as single field but combines multiple fields with an OR operator. Useful when both "created" and "last updated" timestamp fields exist. Separate fields with a comma. |
| **Concatenate fields** | Same as multiple fields but concatenates fields together rather than combining with OR. Useful when separate "last updated date" and "last updated time" fields exist. |
| **Use change document table** | Imports rows based on updates in SAP's change document tables (CDHDR and CDPOS). Useful when the target table lacks a monotonically increasing field. Note that inserts may not be captured for some objects. |
| **Use twin or twinjoin table** | Imports rows from the target table when a field in a separate "twin" table meets the incremental condition. A twinjoin table allows the target to be a join of multiple tables. |

The table below shows which incremental types are supported per object type:

| Object type | Single field | Multiple fields | Concatenate fields | Change document table | Twin table | SAP built-in | Replication | Request based |
|-------------|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Table | ✓ | ✓ | ✓ | ✓ | ✓ | | | ✓ |
| Remote Table | ✓ | ✓ | ✓ | ✓ | ✓ | | | ✓ |
| InfoProvider | ✓ | ✓ | | | | | | ✓ |
| Remote InfoProvider | ✓ | ✓ | | | | | | ✓ |
| SLT | | | | | | | ✓ | |
| Extractor | | | | | | ✓ | | |

:::callout{theme="neutral"}
Incremental updates are not supported for BEx queries or Functions. All syncs for these object types are full extracts.
:::

The incremental field should ideally be a monotonically increasing value. The system uses a "greater than or equal to" comparison to avoid missing data if a sync runs midway through a given date. As a result, duplicate values may appear in the Foundry dataset and should be removed as a first step in the transformation pipeline.

#### Twin table configuration

The **Incremental Twin Table** setting specifies the twin table. The **Incremental Twin Mapping** setting defines the join conditions between the primary and twin tables.
Mapping syntax:

```
{PRIMARY_TABLE_NAME}-{FIELD_NAME}={TWIN_TABLE_NAME}-{FIELD_NAME}
```

Multiple join conditions can be combined with a semicolon (AND operator).

#### Request-based incremental for InfoProviders

In SAP BW, DSOs and InfoCubes are loaded using Data Transfer Processes (DTPs). Each DTP creates a loading request, and the Connector uses these requests to capture changed data.

:::callout{theme="warning"}
This feature is only supported for non-compressed requests. Requests must not be compressed before loading to Foundry. If a request is compressed before loading, the sync will fail and the initial load must be repeated.
:::

Configure via the **Advanced** tab:

```yaml
type: magritte-sap-source-adapter
sapType: infoprovider
obj: <technical-name-of-infoprovider>
incrementalType: REQUEST
```

#### Reset incremental state

To force a full reload and re-initialize incremental ingest:

1. Switch to the **Advanced** tab in the sync configuration.
2. Add `resetIncrementalState: true` to the YAML.
3. Set the transaction type to **SNAPSHOT** (keep any `incremental*` parameters in place).
4. Run the sync. This performs a full snapshot, replacing all files in the dataset.
5. Remove `resetIncrementalState: true` from the YAML.
6. Set the transaction type back to **APPEND**.

Subsequent syncs will resume incremental appends as normal.

### Sync parameters

The following parameters are available in the **Extras** tab or via the **Advanced** YAML view.

#### General parameters

| Parameter | Applicable to | Description |
|-----------|--------------|-------------|
| **Drop columns** | ERP Table, Remote ERP Table | Excludes selected columns before extraction. Improves performance and prevents ingestion of sensitive or unnecessary fields. |
| **Timestamp** | All | Adds `/PALANTIR/TIMESTAMP` (sync run time) and `/PALANTIR/ROWNO` (record order within a sync) columns. Useful for deduplicating records downstream. `/PALANTIR/ROWNO` is only meaningful when using SLT or CDPOS/CDHDR incremental mode — a higher value indicates a more recent change. |
| **Page size** | All | Rows returned per page. Default is 50,000. Values below the default have no effect; reducing the default requires a system call to the SAP add-on. |
| **Retry count** | All | Number of retries when a request fails due to a resource shortage. |
| **Retry delay** | All | Delay in seconds between retry attempts. |
| **Param name** | Function | Selects which output table to write to the Foundry dataset when a function returns multiple output parameters. |
| **Depth** | ERP Table Data Model | Number of relationship levels to follow. Use `1` for first-order, `2` for second-order, and so on. |
| **Trace logging** | All | Set to **On** to enable trace logging for this sync. |
| **Fetch option** | SLT | **XML** fetches using zipped data (faster). **Direct** fetches as a string. Use Direct if you encounter data content errors with XML. |
| [**Debug logging**](#debug-logging) | All | Enables debug logging. Starts a background process in SAP for the sync duration — can drain resources. Use with caution. |
| [**Continuous resource check**](#continuous-resource-check) | All | Controls whether all paging requests or only the initial request are subject to a resource check. |
| [**Resource check**](#resource-check) | All | Disabling removes all resource checks. Can put excess load on SAP. Use with caution. |
| [**Filter**](#filter) | All | Filters extracted data using SAP field values and operators. Supports [dynamic filter keywords](#dynamic-filters). |
| [**Advanced YAML parameters**](#advanced-yaml-parameters) | Varies | `maxRowsPerSync`, `bexSettings`, `ignoreUnexpectedValues`, `outputSettingsOverride`. |

#### Debug logging

:::callout{theme="danger"}
Debug logging starts a background process in the SAP system that runs during the sync. This can drain resources and impact other users. Use with caution.
:::

Set to **On** to enable debug logging for this sync.

#### Continuous resource check

When **On**, all paging requests are subject to a resource check (memory, CPU). When **Off**, only the initial page request is checked. See [performance parameters](/docs/foundry/sap/install-sap-connector/#performance-parameters) for details.

#### Resource check

:::callout{theme="danger"}
Disabling the resource check causes syncs to run regardless of available memory, CPU, and processes. This can put excess load on the SAP system. Use with caution.
:::

Set to **Off** to disable all resource checks for this sync.

#### Filter

Filters the data extracted from SAP. All field names must match the data dictionary.

| Operator | Meaning |
|----------|---------|
| `,` | OR |
| `;` | AND |
| `:` | Between |
| `=` | Equals |
| `!=` | Not equals |
| `>`, `>=`, `<`, `<=` | Comparison |
| `*` | Wildcard |

Examples:

* Price between 500 and 650: `PRICE=500:650`
* Customer A, B, or C: `CUSTOMER=A,B,C`
* Price between 500 and 650 AND customer A, B, or C: `PRICE=500:650;CUSTOMER=A,B,C`
* Material starting with PAL, DIS, or SAP: `MATERIAL=PAL*,DIS*,SAP*`
* Date on or after 9 August 2019 (format YYYYMMDD): `DATE>=20190809`

#### Dynamic filters

Dynamic filters use special keywords and functions to create more flexible filter expressions. Available from add-on version SP26 and later.

**Fixed keywords**

| Keyword | Description |
|---------|-------------|
| `[CURRENTYEAR]` | Current year in `YYYY` format. |
| `[TODAY]` | Today's date in `YYYYMMDD` format. |
| `[LASTDAYOFMONTH]` | Last day of the current month in `YYYYMMDD` format. |
| `[LASTDAYOFLASTMONTH]` | Last day of the previous month in `YYYYMMDD` format. |
| `[FIRSTDAYOFMONTH]` | First day of the current month in `YYYYMMDD` format. |
| `[FIRSTDAYOFLASTMONTH]` | First day of the previous month in `YYYYMMDD` format. |

**Date calculation functions**

| Function | Description |
|----------|-------------|
| `[ADDDAY]` | Adds days to the selected date. Example: `[ADDDAY(22102022,1)]` → `23102022`. |
| `[ADDMONTH]` | Adds months to the selected date. |
| `[ADDYEAR]` | Adds years to the selected date. |
| `[GETMONTH]` | Returns the month of the selected date as a 2-digit value (01–12). |
| `[GETDAY]` | Returns the day of the month as a 2-digit value. |
| `[GETYEAR]` | Returns the year of the selected date. |

Functions can be used directly with fixed keywords or nested:

* Single function: `[ADDDAY([TODAY], 1)]`
* Nested: `[GETDAY([ADDDAY([FIRSTDAYOFMONTH], -1)])]`

Examples:

* Records after today: `BUDAT>[TODAY]`
* Records after the last day of the previous month: `BUDAT>[ADDDAY([FIRSTDAYOFMONTH], -1)]`

#### Advanced YAML parameters

The following parameters require the **Advanced** tab and have no Basic view equivalent.

* `maxRowsPerSync` (SLT only): Limits the number of rows returned per sync run (approximate). Useful for splitting the initial sync of a very large table into smaller runs:

```yaml
maxRowsPerSync: 500000
```

* `bexSettings` (BEx only): Configures BEx query paging. Available from Connector version SP22 onward:

```yaml
bexSettings:
  bexPaging: true
  bexMemberLimit: 10
```

* `bexPaging`: Enables paging using automatically generated filters. Default is `false`.
* `bexMemberLimit`: Threshold for filter candidate selection. InfoObjects with more members than this value are excluded from filter generation. Default is `200`. Minimum is `2`.

-`ignoreUnexpectedValues`: If a sync fails with `Unexpected value encountered in SAP data Failed to parse value XXX in field YYY`, a date or number value cannot be parsed. To continue syncing and set unparsable values to null:

```yaml
ignoreUnexpectedValues: true
```

A warning is logged at the end of the sync with a summary of parse exceptions.

:::callout{theme="warning"}
This setting has no Basic view equivalent. If you switch back to the Basic view, this setting will be lost.
:::

-`outputSettingsOverride`: Overrides the source-level Parquet file size setting for a specific sync:

```yaml
outputSettingsOverride:
  maxFileSize:
    type: rows
    rows:
      max: 10000
```

```yaml
outputSettingsOverride:
  maxFileSize:
    type: bytes
    bytes:
      approximateMax: 400MB
```

:::callout{theme="warning"}
Specifying a maximum size in bytes is approximate — the resulting file sizes may be slightly smaller or larger. The byte value must be at least twice the in-memory buffer size of the Parquet writer, which defaults to 128 MB.
:::

## Streaming syncs

:::callout{theme="neutral" title="Beta"}
Streaming syncs from SAP are in the [beta](/docs/foundry/platform-overview/development-life-cycle/) phase of development and may not be available on your enrollment. Functionality may change during active development.
:::

Streaming syncs are only supported for connections [via an SAP SLT Replication Server](/docs/foundry/sap/architecture/#connecting-to-an-sap-erp-system-via-an-sap-slt-replication-server) and require a source configured with an explicit SLT connection type (see [Enable streaming syncs](#enable-streaming-syncs-slt-only) above).

Each streaming sync creates and subscribes to its own Operational Delta Queue (ODQ) in the SLT Replication Server. Foundry polls the queue periodically (default interval: 1 second):

* If the queue is empty, no further requests are made until the next poll.
* If there are 50,000 records or fewer on the queue, they are consumed synchronously.
* If there are more than 50,000 records, consumption is paginated.

For lowest latency, the SLT Replication Server should have at least as many available dialog work processes as there are active streaming syncs.

### Create a streaming sync

1. Open the SAP source. On the **Overview** page, scroll down to the streaming syncs table and select **+ Create streaming sync**.
2. Enter the name of the SAP table to stream.
3. Choose a location for the output streaming dataset.
   :::callout{theme="warning"}
   Before proceeding, ensure the preview pane at the bottom of the screen has finished loading. The schema for the streaming dataset is derived from this preview. In some cases, the preview may only display the schema without data — this is sufficient.
   :::

4. Select **Create streaming sync**. You can choose to start the stream immediately or start it manually after creation.
:::callout{theme="neutral"}
To ensure a stream automatically restarts after Data Connection agent or SAP system downtime, [set a schedule](/docs/foundry/building-pipelines/create-schedule/) on the streaming dataset with a 1-minute time trigger.
:::

### Throughput and partition keys

Switching the throughput setting from **Normal** to **Very high** may improve performance but increases the number of partitions used. When more than one partition is used, partition keys must be set to guarantee ordering between unique records from SAP. These keys should correspond to the primary key of the table in SAP.

## Webhooks

SAP webhooks allow you to write data back to SAP by invoking Business APIs (BAPIs) from Foundry. See [Webhooks](/docs/foundry/data-connection/webhooks-overview/) for an overview of how to set up a webhook.

:::callout{theme="success"}
SAP webhooks support [Foundry worker](/docs/foundry/data-connection/core-concepts/#foundry-worker) connections in Foundry-managed cloud compute. We recommend this runtime for SAP webhooks instead of executing them through a [data connection agent](/docs/foundry/data-connection/core-concepts/#agents). Existing SAP sources configured on a Foundry worker automatically benefit from cloud execution with no migration required; SAP sources running on a data connection agent should be [switched to a Foundry worker](/docs/foundry/data-connection/foundry-worker-vs-agent-worker/#switch-source-from-agent-worker-to-foundry-worker) to take advantage of cloud-executed webhooks.
:::

The only task type available for SAP webhooks is `sap-run-function-webhook-task-v0`. The following example invokes `BAPI_SALESORDER_CHANGE` to modify the purchase date for a given sales document:

```json
{
    "function-name": "BAPI_SALESORDER_CHANGE",
    "inputs": {
        "SALESDOCUMENT": {{json sales-doc-id}},
        "ORDER_HEADER_IN": {
            "PURCH_DATE": {{json purchase-date}}
        },
        "ORDER_HEADER_INX": {
            "UPDATEFLAG": "U",
            "PURCH_DATE": "X"
        }
    },
    "output": "RETURN"
}
```

To target a remote SAP system, add a `remote` field to the task body:

```json
{
    ...
    "output": "RETURN",
    "remote": {
        "context": "<SAP_CONTEXT_NAME>"
    }
}
```

## Related documentation

The following guides cover workflows that involve both SAP-side and Foundry-side configuration:

* [Extract long text from SAP](/docs/foundry/sap/extract-long-text/): Decompress and ingest long texts from the `STXL` table.
* [Configure custom authorizations and role management](/docs/foundry/sap/configure-custom-authorizations/): Set up custom authorization roles for the SAP add-on.
* [Configure extractors](/docs/foundry/sap/configure-extractors/): Configure SAP BW Business Content extractors.
* [Ingest HANA views from SAP](/docs/foundry/sap/ingest-hana-views/): Publish and ingest HANA external views.
* [User-attributed SAP writeback with OAuth 2.0](/docs/foundry/sap/oauth2-writeback/): Configure OAuth 2.0 for named-user writeback to SAP.
