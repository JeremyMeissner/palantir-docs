---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-resources/transactions/commit-transaction/"
title: "Commit Transaction \u2022 API Reference"
---
# Commit Transaction

## Endpoint

Commits an open Transaction. File modifications made on this Transaction are preserved and the Branch is
updated to point to the Transaction.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-write`.

**operationId:** v1.commitTransaction

**path:** /api/v1/datasets/{datasetRid}/transactions/{transactionRid}/commit

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of the Dataset that contains the Transaction. |
| transactionRid | stringType | True | The Resource Identifier (RID) of the Transaction. |

### Response

#### Body

An operation that modifies the files within a dataset.

**name:** Transaction

**example:** {"rid":"ri.foundry.main.transaction.abffc380-ea68-4843-9be1-9f44d2565496","transactionType":"SNAPSHOT","status":"COMMITTED","createdTime":"2022-10-10T12:20:15.166Z","closedTime":"2022-10-10T12:23:11.152Z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The Resource Identifier (RID) of a Transaction. |
| transactionType | enumType | True | The type of a Transaction. |
| status | enumType | True | The status of a Transaction. |
| createdTime | stringType | True | The timestamp when the transaction was created, in ISO 8601 timestamp format. |
| closedTime | stringType | False | The timestamp when the transaction was closed, in ISO 8601 timestamp format. |

**example:** {"rid":"ri.foundry.main.transaction.abffc380-ea68-4843-9be1-9f44d2565496","transactionType":"SNAPSHOT","status":"COMMITTED","createdTime":"2022-10-10T12:20:15.166Z","closedTime":"2022-10-10T12:23:11.152Z"}

### Error Responses

| name | description |
| --- | --- |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
| TransactionNotFound | The requested transaction could not be found on the dataset, or the client token does not have access to it. |
| CommitTransactionPermissionDenied | The provided token does not have permission to commit the given transaction on the given dataset. |
| TransactionNotOpen | The given transaction is not open. |
