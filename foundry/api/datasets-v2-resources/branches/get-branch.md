---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/branches/get-branch/"
title: "Get Branch \u2022 API Reference"
---
# Get Branch

## Endpoint

Get a Branch of a Dataset.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-read`.

**operationId:** v2.getBranch

**path:** /api/v2/datasets/{datasetRid}/branches/{branchName}

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of a Dataset. |
| branchName | stringType | True | The name of a Branch. |

### Response

#### Body

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
