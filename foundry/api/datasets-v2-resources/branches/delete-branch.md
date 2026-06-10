---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/branches/delete-branch/"
title: "Delete Branch \u2022 API Reference"
---
# Delete Branch

## Endpoint

Deletes the Branch with the given BranchName.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-write`.

**operationId:** v2.deleteBranch

**path:** /api/v2/datasets/{datasetRid}/branches/{branchName}

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of a Dataset. |
| branchName | stringType | True | The name of a Branch. |

### Error Responses

| name | description |
| --- | --- |
| BranchNotFound | The requested branch could not be found, or the client token does not have access to it. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
| InvalidBranchName | The requested branch name cannot be used. Branch names cannot be empty and must not look like RIDs or UUIDs. |
| DeleteBranchPermissionDenied | Could not delete the Branch. |
