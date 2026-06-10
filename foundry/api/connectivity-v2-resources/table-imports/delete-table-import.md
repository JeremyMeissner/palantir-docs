---
source_url: "https://www.palantir.com/docs/foundry/api/connectivity-v2-resources/table-imports/delete-table-import/"
title: "Delete Table Import \u2022 API Reference"
---
# Delete Table Import

## Endpoint

Delete the TableImport with the specified RID.
Deleting the table import does not delete the destination dataset but the dataset will no longer
be updated by this import.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:connectivity-table-import-write`.

**operationId:** v2.deleteTableImport

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

### Error Responses

| name | description |
| --- | --- |
| DeleteTableImportPermissionDenied | Could not delete the TableImport. |
| TableImportNotFound | The given TableImport could not be found. |
