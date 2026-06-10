---
source_url: "https://www.palantir.com/docs/foundry/api/connectivity-v2-resources/table-imports/replace-table-import/"
title: "Replace Table Import \u2022 API Reference"
---
# Replace Table Import

## Endpoint

Replace the TableImport with the specified rid.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:connectivity-table-import-write`.

**operationId:** v2.replaceTableImport

**path:** /api/v2/connectivity/connections/{connectionRid}/tableImports/{tableImportRid}

### Operation Type

### Scopes

| name |
| --- |
| api:connectivity-table-import-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| connectionRid | stringType | True | The Resource Identifier (RID) of a Connection (also known as a source). |
| tableImportRid | stringType | True | The Resource Identifier (RID) of a TableImport (also known as a batch sync). |

### Request

#### Body

**name:** ReplaceTableImportRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| importMode | enumType | True | Import mode governs how data is read from an external system, and written into a Foundry dataset.   SNAPSHOT: Defines a new dataset state consisting only of data from a particular import execution. APPEND: Purely additive and yields data from previous import executions in addition to newly added data. |
| displayName | stringType | True |  |
| allowSchemaChanges | booleanType | False | Allow the TableImport to succeed if the schema of imported rows does not match the existing dataset's schema. Defaults to false for new table imports. |
| config | unionType | True | The import configuration for a specific [connector type](/docs/foundry/data-integration/source-type-overview). |

**example:** {"importMode":"SNAPSHOT","displayName":"My table import","allowSchemaChanges":true,"config":{"type":"jdbcImportConfig","query":"SELECT * FROM table"}}

### Response

#### Body

The replaced TableImport

**name:** TableImport

**example:** {"datasetRid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","importMode":"SNAPSHOT","displayName":"My table import","allowSchemaChanges":true,"connectionRid":"ri.magritte..source.c078b71b-92f9-41b6-b0df-3760f411120b","branchName":"master","rid":"ri.magritte..extract.27bb4f2b-63b8-44b8-a579-4e2bd65ba158","config":{"type":"jdbcImportConfig","query":"SELECT * FROM table"}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The Resource Identifier (RID) of a TableImport (also known as a batch sync). |
| connectionRid | stringType | True | The RID of the Connection (also known as a source) that the Table Import uses to import data. |
| datasetRid | stringType | True | The RID of the output dataset. Can not be modified after the table import is created. |
| branchName | stringType | False | The branch name in the output dataset that will contain the imported data. Defaults to `master` for most enrollments. Can not be modified after the table import is created. |
| displayName | stringType | True |  |
| importMode | enumType | True | Import mode governs how data is read from an external system, and written into a Foundry dataset.   SNAPSHOT: Defines a new dataset state consisting only of data from a particular import execution. APPEND: Purely additive and yields data from previous import executions in addition to newly added data. |
| allowSchemaChanges | booleanType | True | Allow the TableImport to succeed if the schema of imported rows does not match the existing dataset's schema. Defaults to false for new table imports. |
| config | unionType | True | The import configuration for a specific [connector type](/docs/foundry/data-integration/source-type-overview). |

**example:** {"datasetRid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","importMode":"SNAPSHOT","displayName":"My table import","allowSchemaChanges":true,"connectionRid":"ri.magritte..source.c078b71b-92f9-41b6-b0df-3760f411120b","branchName":"master","rid":"ri.magritte..extract.27bb4f2b-63b8-44b8-a579-4e2bd65ba158","config":{"type":"jdbcImportConfig","query":"SELECT * FROM table"}}

### Error Responses

| name | description |
| --- | --- |
| TableImportTypeNotSupported | The specified table import type is not yet supported in the Platform API. |
| TableImportNotSupportedForConnection | The specified connection does not support creating or replacing a table import with the specified config. |
| ConnectionDetailsNotDetermined | Details of the connection (such as which types of import it supports) could not be determined. |
| ReplaceTableImportPermissionDenied | Could not replace the TableImport. |
| TableImportNotFound | The given TableImport could not be found. |
| ConnectionNotFound | The given Connection could not be found. |
