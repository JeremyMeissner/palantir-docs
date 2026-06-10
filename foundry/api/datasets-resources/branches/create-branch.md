---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-resources/branches/create-branch/"
title: "Create Branch \u2022 API Reference"
---
# Create Branch

## Endpoint

Creates a branch on an existing dataset. A branch may optionally point to a (committed) transaction.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-write`.

**operationId:** v1.createBranch

**path:** /api/v1/datasets/{datasetRid}/branches

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of the Dataset on which to create the Branch. |

### Request

#### Body

**name:** CreateBranchRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| branchId | stringType | True | The identifier (name) of a Branch. |
| transactionRid | stringType | False | The Resource Identifier (RID) of a Transaction. |

**example:** {"branchId":"my-branch"}

### Response

#### Body

A Branch of a Dataset.

**name:** Branch

**example:** {"branchId":"my-branch"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| branchId | stringType | True | The identifier (name) of a Branch. |
| transactionRid | stringType | False | The Resource Identifier (RID) of a Transaction. |

**example:** {"branchId":"my-branch"}

### Error Responses

| name | description |
| --- | --- |
| InvalidBranchId | The requested branch name cannot be used. Branch names cannot be empty and must not look like RIDs or UUIDs. |
| TransactionNotCommitted | The given transaction has not been committed. |
| TransactionNotFound | The requested transaction could not be found on the dataset, or the client token does not have access to it. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
| CreateBranchPermissionDenied | The provided token does not have permission to create a branch of this dataset. |
| BranchAlreadyExists | The branch cannot be created because a branch with that name already exists. |
