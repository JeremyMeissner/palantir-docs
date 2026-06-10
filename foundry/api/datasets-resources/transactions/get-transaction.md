---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-resources/transactions/get-transaction/"
title: "Get Transaction \u2022 API Reference"
---
# Get Transaction

## Endpoint

Gets a Transaction of a Dataset.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-read`.

**operationId:** v1.getTransaction

**path:** /api/v1/datasets/{datasetRid}/transactions/{transactionRid}

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of the Dataset that contains the Transaction. |
| transactionRid | stringType | True | The Resource Identifier (RID) of the Transaction. |

### Response

#### Body

An operation that modifies the files within a dataset.

**name:** Transaction

**example:** {"rid":"ri.foundry.main.transaction.abffc380-ea68-4843-9be1-9f44d2565496","transactionType":"SNAPSHOT","status":"OPEN","createdTime":"2022-10-10T12:20:15.166Z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The Resource Identifier (RID) of a Transaction. |
| transactionType | enumType | True | The type of a Transaction. |
| status | enumType | True | The status of a Transaction. |
| createdTime | stringType | True | The timestamp when the transaction was created, in ISO 8601 timestamp format. |
| closedTime | stringType | False | The timestamp when the transaction was closed, in ISO 8601 timestamp format. |

**example:** {"rid":"ri.foundry.main.transaction.abffc380-ea68-4843-9be1-9f44d2565496","transactionType":"SNAPSHOT","status":"OPEN","createdTime":"2022-10-10T12:20:15.166Z"}

### Error Responses

| name | description |
| --- | --- |
| TransactionNotFound | The requested transaction could not be found on the dataset, or the client token does not have access to it. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
