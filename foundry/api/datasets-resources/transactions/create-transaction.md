---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-resources/transactions/create-transaction/"
title: "Create Transaction \u2022 API Reference"
---
# Create Transaction

## Endpoint

Creates a Transaction on a Branch of a Dataset.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-write`.

**operationId:** v1.createTransaction

**path:** /api/v1/datasets/{datasetRid}/transactions

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of the Dataset on which to create the Transaction. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branchId | stringType | False | The identifier (name) of the Branch on which to create the Transaction. Defaults to `master` for most enrollments. |

### Request

#### Body

**name:** CreateTransactionRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| transactionType | enumType | False | The type of a Transaction. |

**example:** {"transactionType":"SNAPSHOT"}

### Response

#### Body

An operation that modifies the files within a dataset.

**name:** Transaction

**example:** {"rid":"ri.foundry.main.transaction.abffc380-ea68-4843-9be1-9f44d2565496","transactionType":"SNAPSHOT","status":"OPEN","createdTime":"2022-10-10T12:23:11.152Z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The Resource Identifier (RID) of a Transaction. |
| transactionType | enumType | True | The type of a Transaction. |
| status | enumType | True | The status of a Transaction. |
| createdTime | stringType | True | The timestamp when the transaction was created, in ISO 8601 timestamp format. |
| closedTime | stringType | False | The timestamp when the transaction was closed, in ISO 8601 timestamp format. |

**example:** {"rid":"ri.foundry.main.transaction.abffc380-ea68-4843-9be1-9f44d2565496","transactionType":"SNAPSHOT","status":"OPEN","createdTime":"2022-10-10T12:23:11.152Z"}

### Error Responses

| name | description |
| --- | --- |
| OpenTransactionAlreadyExists | A transaction is already open on this dataset and branch. A branch of a dataset can only have one open transaction at a time. |
| CreateTransactionPermissionDenied | The provided token does not have permission to create a transaction on this dataset. |
| InvalidBranchId | The requested branch name cannot be used. Branch names cannot be empty and must not look like RIDs or UUIDs. |
| BranchNotFound | The requested branch could not be found, or the client token does not have access to it. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
