---
source_url: "https://www.palantir.com/docs/foundry/api/connectivity-v2-resources/file-imports/delete-file-import/"
title: "Delete File Import \u2022 API Reference"
---
# Delete File Import

## Endpoint

Delete the FileImport with the specified RID.
Deleting the file import does not delete the destination dataset but the dataset will no longer
be updated by this import.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:connectivity-file-import-write`.

**operationId:** v2.deleteFileImport

**path:** /api/v2/connectivity/connections/{connectionRid}/fileImports/{fileImportRid}

### Operation Type

### Scopes

| name |
| --- |
| api:connectivity-file-import-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| connectionRid | stringType | True | The Resource Identifier (RID) of a Connection (also known as a source). |
| fileImportRid | stringType | True | The Resource Identifier (RID) of a FileImport (also known as a batch sync). |

### Error Responses

| name | description |
| --- | --- |
| DeleteFileImportPermissionDenied | Could not delete the FileImport. |
| FileImportNotFound | The given FileImport could not be found. |
