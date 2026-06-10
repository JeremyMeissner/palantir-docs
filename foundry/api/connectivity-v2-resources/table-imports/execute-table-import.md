---
source_url: "https://www.palantir.com/docs/foundry/api/connectivity-v2-resources/table-imports/execute-table-import/"
title: "Execute Table Import \u2022 API Reference"
---
# Execute Table Import

## Endpoint

Executes the TableImport, which runs asynchronously as a [Foundry Build](/docs/foundry/data-integration/builds/).
The returned BuildRid can be used to check the status via the Orchestration API.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:connectivity-table-import-execute`.

**operationId:** v2.executeTableImport

**path:** /api/v2/connectivity/connections/{connectionRid}/tableImports/{tableImportRid}/execute

### Operation Type

### Scopes

| name |
| --- |
| api:connectivity-table-import-execute |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| connectionRid | stringType | True | The Resource Identifier (RID) of a Connection (also known as a source). |
| tableImportRid | stringType | True | The Resource Identifier (RID) of a TableImport (also known as a batch sync). |

### Response

#### Body

The RID of a Build.

**name:** BuildRid

##### Format

**example:** ri.foundry.main.build.a4386b7e-d546-49be-8a36-eefc355f5c58

**example:** ri.foundry.main.build.a4386b7e-d546-49be-8a36-eefc355f5c58

### Error Responses

| name | description |
| --- | --- |
| ExecuteTableImportPermissionDenied | Could not execute the TableImport. |
| TableImportNotFound | The given TableImport could not be found. |
