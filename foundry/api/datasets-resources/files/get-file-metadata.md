---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-resources/files/get-file-metadata/"
title: "Get File Metadata \u2022 API Reference"
---
# Get File Metadata

## Endpoint

Gets metadata about a File contained in a Dataset. By default this retrieves the file's metadata from the latest
view of the default branch - `master` for most enrollments.

#### Advanced Usage

See [Datasets Core Concepts](/docs/foundry/data-integration/datasets/) for details on using branches and transactions. 

To **get a file's metadata from a specific Branch** specify the Branch's identifier as `branchId`. This will 
retrieve metadata for the most recent version of the file since the latest snapshot transaction, or the earliest
ancestor transaction of the branch if there are no snapshot transactions.

To **get a file's metadata from the resolved view of a transaction** specify the Transaction's resource identifier
as `endTransactionRid`. This will retrieve metadata for the most recent version of the file since the latest snapshot
transaction, or the earliest ancestor transaction if there are no snapshot transactions.

To **get a file's metadata from the resolved view of a range of transactions** specify the the start transaction's
resource identifier as `startTransactionRid` and the end transaction's resource identifier as `endTransactionRid`.
This will retrieve metadata for the most recent version of the file since the `startTransactionRid` up to the 
`endTransactionRid`. Behavior is undefined when the start and end transactions do not belong to the same root-to-leaf path.

To **get a file's metadata from a specific transaction** specify the Transaction's resource identifier as both the 
`startTransactionRid` and `endTransactionRid`.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-read`.

**operationId:** v1.getFileMetadata

**path:** /api/v1/datasets/{datasetRid}/files/{filePath}

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of the Dataset that contains the File. |
| filePath | stringType | True | The File's path within the Dataset. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branchId | stringType | False | The identifier (name) of the Branch that contains the File. Defaults to `master` for most enrollments. |
| startTransactionRid | stringType | False | The Resource Identifier (RID) of the start Transaction. |
| endTransactionRid | stringType | False | The Resource Identifier (RID) of the end Transaction. |

### Response

#### Body

**name:** File

**example:** {"path":"q3-data/my-file.csv","transactionRid":"ri.foundry.main.transaction.bf9515c2-02d4-4703-8f84-c3b3c190254d","sizeBytes":"74930","updatedTime":"2022-10-10T16:44:55.192Z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| path | stringType | True | The path to a File within Foundry. Paths are relative and must not start with a leading slash. Examples: `my-file.txt`, `path/to/my-file.jpg`, `dataframe.snappy.parquet`. |
| transactionRid | stringType | True | The Resource Identifier (RID) of a Transaction. |
| sizeBytes | stringType | False |  |
| updatedTime | stringType | True |  |

**example:** {"path":"q3-data/my-file.csv","transactionRid":"ri.foundry.main.transaction.bf9515c2-02d4-4703-8f84-c3b3c190254d","sizeBytes":"74930","updatedTime":"2022-10-10T16:44:55.192Z"}

### Error Responses

| name | description |
| --- | --- |
| InvalidParameterCombination | The given parameters are individually valid but cannot be used in the given combination. |
| FileNotFoundOnTransactionRange | The requested file could not be found on the given transaction range, or the client token does not have access to it. |
| FileNotFoundOnBranch | The requested file could not be found on the given branch, or the client token does not have access to it. |
| InvalidBranchId | The requested branch name cannot be used. Branch names cannot be empty and must not look like RIDs or UUIDs. |
| BranchNotFound | The requested branch could not be found, or the client token does not have access to it. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
| TransactionNotFound | The requested transaction could not be found on the dataset, or the client token does not have access to it. |
