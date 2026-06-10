---
source_url: "https://www.palantir.com/docs/foundry/api/connectivity-v2-resources/table-imports/list-table-imports/"
title: "List Table Imports \u2022 API Reference"
---
# List Table Imports

## Endpoint

Lists all table imports defined for this connection.
Only table imports that the user has permissions to view will be returned.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:connectivity-table-import-read`.

**operationId:** v2.listTableImports

**path:** /api/v2/connectivity/connections/{connectionRid}/tableImports

### Operation Type

### Scopes

| name |
| --- |
| api:connectivity-table-import-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| connectionRid | stringType | True | The Resource Identifier (RID) of a Connection (also known as a source). |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

### Response

#### Body

**name:** ListTableImportsResponse

**example:** {"data":[{"datasetRid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","importMode":"SNAPSHOT","displayName":"My table import","allowSchemaChanges":true,"connectionRid":"ri.magritte..source.c078b71b-92f9-41b6-b0df-3760f411120b","branchName":"master","rid":"ri.magritte..extract.27bb4f2b-63b8-44b8-a579-4e2bd65ba158","config":{"type":"jdbcImportConfig","query":"SELECT * FROM table"}}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"datasetRid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","importMode":"SNAPSHOT","displayName":"My table import","allowSchemaChanges":true,"connectionRid":"ri.magritte..source.c078b71b-92f9-41b6-b0df-3760f411120b","branchName":"master","rid":"ri.magritte..extract.27bb4f2b-63b8-44b8-a579-4e2bd65ba158","config":{"type":"jdbcImportConfig","query":"SELECT * FROM table"}}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| ConnectionNotFound | The given Connection could not be found. |
