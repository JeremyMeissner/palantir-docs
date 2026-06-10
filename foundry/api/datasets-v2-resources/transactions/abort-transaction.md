---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/transactions/abort-transaction/"
title: "Abort Transaction \u2022 API Reference"
---
# Abort Transaction

## Endpoint

Aborts an open Transaction. File modifications made on this Transaction are not preserved and the Branch is
not updated.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-write`.

**operationId:** v2.abortTransaction

**path:** /api/v2/datasets/{datasetRid}/transactions/{transactionRid}/abort

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of a Dataset. |
| transactionRid | stringType | True | The Resource Identifier (RID) of a Transaction. |

### Response

#### Body

**name:** Transaction

**example:** {"transactionType":"APPEND","createdTime":"2020-09-30T14:30:00Z","rid":"ri.foundry.main.transaction.0a0207cb-26b7-415b-bc80-66a3aa3933f4","closedTime":"2020-09-30T21:00:00Z","status":"COMMITTED"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The Resource Identifier (RID) of a Transaction. |
| transactionType | enumType | True | The type of a Transaction. |
| status | enumType | True | The status of a Transaction. |
| createdTime | stringType | True | The timestamp when the transaction was created, in ISO 8601 timestamp format. |
| closedTime | stringType | False | The timestamp when the transaction was closed, in ISO 8601 timestamp format. |

**example:** {"transactionType":"APPEND","createdTime":"2020-09-30T14:30:00Z","rid":"ri.foundry.main.transaction.0a0207cb-26b7-415b-bc80-66a3aa3933f4","closedTime":"2020-09-30T21:00:00Z","status":"COMMITTED"}

### Error Responses

| name | description |
| --- | --- |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
| TransactionNotFound | The requested transaction could not be found on the dataset, or the client token does not have access to it. |
| TransactionNotOpen | The given transaction is not open. |
| AbortTransactionPermissionDenied | Could not abort the Transaction. |
