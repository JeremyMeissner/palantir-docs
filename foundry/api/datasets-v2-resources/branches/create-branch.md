---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/branches/create-branch/"
title: "Create Branch \u2022 API Reference"
---
# Create Branch

## Endpoint

Creates a branch on an existing dataset. A branch may optionally point to a (committed) transaction.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-write`.

**operationId:** v2.createBranch

**path:** /api/v2/datasets/{datasetRid}/branches

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of a Dataset. |

### Request

#### Body

**name:** CreateBranchRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| transactionRid | stringType | False | The most recent OPEN or COMMITTED transaction on the branch. This will never be an ABORTED transaction. |
| name | stringType | True | The name of a Branch. |

**example:** {"transactionRid":"ri.foundry.main.transaction.0a0207cb-26b7-415b-bc80-66a3aa3933f4","name":"master"}

### Response

#### Body

The created Branch

**name:** Branch

**example:** {"transactionRid":"ri.foundry.main.transaction.0a0207cb-26b7-415b-bc80-66a3aa3933f4","name":"master"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| name | stringType | True | The name of a Branch. |
| transactionRid | stringType | False | The most recent OPEN or COMMITTED transaction on the branch. This will never be an ABORTED transaction. |

**example:** {"transactionRid":"ri.foundry.main.transaction.0a0207cb-26b7-415b-bc80-66a3aa3933f4","name":"master"}

### Error Responses

| name | description |
| --- | --- |
| BranchNotFound | The requested branch could not be found, or the client token does not have access to it. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
| TransactionNotCommitted | The given transaction has not been committed. |
| TransactionNotFound | The requested transaction could not be found on the dataset, or the client token does not have access to it. |
| CreateBranchPermissionDenied | The provided token does not have permission to create a branch of this dataset. |
| BranchAlreadyExists | The branch cannot be created because a branch with that name already exists. |
| InvalidBranchName | The requested branch name cannot be used. Branch names cannot be empty and must not look like RIDs or UUIDs. |
