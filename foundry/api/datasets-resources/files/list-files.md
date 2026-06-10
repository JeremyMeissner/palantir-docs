---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-resources/files/list-files/"
title: "List Files \u2022 API Reference"
---
# List Files

## Endpoint

Lists Files contained in a Dataset. By default files are listed on the latest view of the default 
branch - `master` for most enrollments.

This endpoint currently does not support views (virtual datasets composed of other datasets). For more information, refer to the [views documentation](/docs/foundry/data-integration/views).

#### Advanced Usage

See [Datasets Core Concepts](/docs/foundry/data-integration/datasets/) for details on using branches and transactions.

To **list files on a specific Branch** specify the Branch's identifier as `branchId`. This will include the most
recent version of all files since the latest snapshot transaction, or the earliest ancestor transaction of the 
branch if there are no snapshot transactions.

To **list files on the resolved view of a transaction** specify the Transaction's resource identifier
as `endTransactionRid`. This will include the most recent version of all files since the latest snapshot
transaction, or the earliest ancestor transaction if there are no snapshot transactions.

To **list files on the resolved view of a range of transactions** specify the the start transaction's resource
identifier as `startTransactionRid` and the end transaction's resource identifier as `endTransactionRid`. This
will include the most recent version of all files since the `startTransactionRid` up to the `endTransactionRid`.
Note that an intermediate snapshot transaction will remove all files from the view. Behavior is undefined when 
the start and end transactions do not belong to the same root-to-leaf path.

To **list files on a specific transaction** specify the Transaction's resource identifier as both the 
`startTransactionRid` and `endTransactionRid`. This will include only files that were modified as part of that
Transaction.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-read`.

**operationId:** v1.listFiles

**path:** /api/v1/datasets/{datasetRid}/files

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of the Dataset on which to list Files. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branchId | stringType | False | The identifier (name) of the Branch on which to list Files. Defaults to `master` for most enrollments. |
| startTransactionRid | stringType | False | The Resource Identifier (RID) of the start Transaction. |
| endTransactionRid | stringType | False | The Resource Identifier (RID) of the end Transaction. |
| pageSize | integerType | False | The desired size of the page to be returned. Defaults to 1,000. See [page sizes](/docs/foundry/api/general/overview/paging/#page-sizes) for details. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

### Response

#### Body

A page of Files and an optional page token that can be used to retrieve the next page.

**name:** ListFilesResponse

**example:** {"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z","data":[{"path":"q3-data/my-file.csv","transactionRid":"ri.foundry.main.transaction.bf9515c2-02d4-4703-8f84-c3b3c190254d","sizeBytes":"74930","updatedTime":"2022-10-10T16:44:55.192Z"},{"path":"q2-data/my-file.csv","transactionRid":"ri.foundry.main.transaction.d8db1cfc-9f8b-4bad-9d8c-00bd818a37c5","sizeBytes":"47819","updatedTime":"2022-07-12T10:12:50.919Z"},{"path":"q2-data/my-other-file.csv","transactionRid":"ri.foundry.main.transaction.d8db1cfc-9f8b-4bad-9d8c-00bd818a37c5","sizeBytes":"55320","updatedTime":"2022-07-12T10:12:46.112Z"}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| data | listType | False |  |

**example:** {"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z","data":[{"path":"q3-data/my-file.csv","transactionRid":"ri.foundry.main.transaction.bf9515c2-02d4-4703-8f84-c3b3c190254d","sizeBytes":"74930","updatedTime":"2022-10-10T16:44:55.192Z"},{"path":"q2-data/my-file.csv","transactionRid":"ri.foundry.main.transaction.d8db1cfc-9f8b-4bad-9d8c-00bd818a37c5","sizeBytes":"47819","updatedTime":"2022-07-12T10:12:50.919Z"},{"path":"q2-data/my-other-file.csv","transactionRid":"ri.foundry.main.transaction.d8db1cfc-9f8b-4bad-9d8c-00bd818a37c5","sizeBytes":"55320","updatedTime":"2022-07-12T10:12:46.112Z"}]}

### Error Responses

| name | description |
| --- | --- |
| InvalidParameterCombination | The given parameters are individually valid but cannot be used in the given combination. |
| InvalidBranchId | The requested branch name cannot be used. Branch names cannot be empty and must not look like RIDs or UUIDs. |
| BranchNotFound | The requested branch could not be found, or the client token does not have access to it. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
| TransactionNotFound | The requested transaction could not be found on the dataset, or the client token does not have access to it. |
