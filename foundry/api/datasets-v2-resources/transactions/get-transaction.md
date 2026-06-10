---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/transactions/get-transaction/"
title: "Get Transaction \u2022 API Reference"
---
# Get Transaction

## Endpoint

Gets a Transaction of a Dataset.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-read`.

**operationId:** v2.getTransaction

**path:** /api/v2/datasets/{datasetRid}/transactions/{transactionRid}

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-read |

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
| TransactionNotFound | The given Transaction could not be found. |
