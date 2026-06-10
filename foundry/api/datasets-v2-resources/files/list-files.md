---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/files/list-files/"
title: "List Files \u2022 API Reference"
---
# List Files

## Endpoint

Lists Files contained in a Dataset. By default files are listed on the latest view of the default 
branch - `master` for most enrollments.
#### Advanced Usage
See [Datasets Core Concepts](/docs/foundry/data-integration/datasets/) for details on using branches and transactions.
To **list files on a specific Branch** specify the Branch's name as `branchName`. This will include the most
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

**operationId:** v2.listFiles

**path:** /api/v2/datasets/{datasetRid}/files

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
| branchName | stringType | False | The name of the Branch on which to list Files. Defaults to `master` for most enrollments. |
| pathPrefix | stringType | False | When present returns only files in the dataset whose path starts with this value. If pathPrefix matches a file exactly, returns just that file. |
| startTransactionRid | stringType | False | The Resource Identifier (RID) of the start Transaction. |
| endTransactionRid | stringType | False | The Resource Identifier (RID) of the end Transaction. |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

### Response

#### Body

**name:** ListFilesResponse

**example:** {"data":[{"path":"2020/09/30/trades.csv","updatedTime":"2020-09-30T12:34:56.789Z","transactionRid":"ri.foundry.main.transaction.0a0207cb-26b7-415b-bc80-66a3aa3933f4"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"path":"2020/09/30/trades.csv","updatedTime":"2020-09-30T12:34:56.789Z","transactionRid":"ri.foundry.main.transaction.0a0207cb-26b7-415b-bc80-66a3aa3933f4"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| BranchNotFound | The requested branch could not be found, or the client token does not have access to it. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
| InvalidParameterCombination | The given parameters are individually valid but cannot be used in the given combination. |
| InvalidPageSize | The provided page size was zero or negative. Page sizes must be greater than zero. |
| TransactionNotFound | The requested transaction could not be found on the dataset, or the client token does not have access to it. |
| InvalidBranchName | The requested branch name cannot be used. Branch names cannot be empty and must not look like RIDs or UUIDs. |
| InvalidFilePath | The provided file path is invalid. Check that the path does not start with a leading slash. |
