---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-resources/branches/get-branch/"
title: "Get Branch \u2022 API Reference"
---
# Get Branch

## Endpoint

Get a Branch of a Dataset.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-read`.

**operationId:** v1.getBranch

**path:** /api/v1/datasets/{datasetRid}/branches/{branchId}

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of the Dataset that contains the Branch. |
| branchId | stringType | True | The identifier (name) of the Branch. |

### Response

#### Body

A Branch of a Dataset.

**name:** Branch

**example:** {"branchId":"master","transactionRid":"ri.foundry.main.transaction.0a0207cb-26b7-415b-bc80-66a3aa3933f4"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| branchId | stringType | True | The identifier (name) of a Branch. |
| transactionRid | stringType | False | The Resource Identifier (RID) of a Transaction. |

**example:** {"branchId":"master","transactionRid":"ri.foundry.main.transaction.0a0207cb-26b7-415b-bc80-66a3aa3933f4"}

### Error Responses

| name | description |
| --- | --- |
| BranchNotFound | The requested branch could not be found, or the client token does not have access to it. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
