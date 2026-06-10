---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-resources/branches/delete-branch/"
title: "Delete Branch \u2022 API Reference"
---
# Delete Branch

## Endpoint

Deletes the Branch with the given BranchId.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-write`.

**operationId:** v1.deleteBranch

**path:** /api/v1/datasets/{datasetRid}/branches/{branchId}

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of the Dataset that contains the Branch. |
| branchId | stringType | True | The identifier (name) of the Branch. |

### Error Responses

| name | description |
| --- | --- |
| DeleteBranchPermissionDenied | The provided token does not have permission to delete the given branch from this dataset. |
| InvalidBranchId | The requested branch name cannot be used. Branch names cannot be empty and must not look like RIDs or UUIDs. |
| BranchNotFound | The requested branch could not be found, or the client token does not have access to it. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
