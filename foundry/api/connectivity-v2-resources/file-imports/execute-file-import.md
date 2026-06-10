---
source_url: "https://www.palantir.com/docs/foundry/api/connectivity-v2-resources/file-imports/execute-file-import/"
title: "Execute File Import \u2022 API Reference"
---
# Execute File Import

## Endpoint

Executes the FileImport, which runs asynchronously as a [Foundry Build](/docs/foundry/data-integration/builds/).
The returned BuildRid can be used to check the status via the Orchestration API.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:connectivity-file-import-execute`.

**operationId:** v2.executeFileImport

**path:** /api/v2/connectivity/connections/{connectionRid}/fileImports/{fileImportRid}/execute

### Operation Type

### Scopes

| name |
| --- |
| api:connectivity-file-import-execute |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| connectionRid | stringType | True | The Resource Identifier (RID) of a Connection (also known as a source). |
| fileImportRid | stringType | True | The Resource Identifier (RID) of a FileImport (also known as a batch sync). |

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
| ExecuteFileImportPermissionDenied | Could not execute the FileImport. |
| FileImportNotFound | The given FileImport could not be found. |
