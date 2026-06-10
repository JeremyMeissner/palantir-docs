---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/datasets/list-transactions-of-dataset/"
title: "List Transactions Of Dataset \u2022 API Reference"
---
# List Transactions Of Dataset

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Get the Transaction history for the given Dataset. When requesting all transactions, the endpoint returns them in reverse chronological order.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-read`.

**operationId:** v2.listTransactionsOfDataset

**path:** /api/v2/datasets/{datasetRid}/transactions

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of a Dataset. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** ListTransactionsOfDatasetResponse

**example:** {"data":[{"transactionType":"APPEND","createdTime":"2020-09-30T14:30:00Z","rid":"ri.foundry.main.transaction.0a0207cb-26b7-415b-bc80-66a3aa3933f4","closedTime":"2020-09-30T21:00:00Z","status":"COMMITTED"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"transactionType":"APPEND","createdTime":"2020-09-30T14:30:00Z","rid":"ri.foundry.main.transaction.0a0207cb-26b7-415b-bc80-66a3aa3933f4","closedTime":"2020-09-30T21:00:00Z","status":"COMMITTED"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| BranchNotFound | The requested branch could not be found, or the client token does not have access to it. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
