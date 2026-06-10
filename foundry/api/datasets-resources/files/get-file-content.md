---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-resources/files/get-file-content/"
title: "Get File Content \u2022 API Reference"
---
# Get File Content

## Endpoint

Gets the content of a File contained in a Dataset. By default this retrieves the file's content from the latest
view of the default branch - `master` for most enrollments.

This endpoint currently does not support views (virtual datasets composed of other datasets). For more information, refer to the [views documentation](/docs/foundry/data-integration/views).

#### Advanced Usage

See [Datasets Core Concepts](/docs/foundry/data-integration/datasets/) for details on using branches and transactions. 

To **get a file's content from a specific Branch** specify the Branch's identifier as `branchId`. This will 
retrieve the content for the most recent version of the file since the latest snapshot transaction, or the
earliest ancestor transaction of the branch if there are no snapshot transactions.

To **get a file's content from the resolved view of a transaction** specify the Transaction's resource identifier
as `endTransactionRid`. This will retrieve the content for the most recent version of the file since the latest
snapshot transaction, or the earliest ancestor transaction if there are no snapshot transactions.

To **get a file's content from the resolved view of a range of transactions** specify the the start transaction's
resource identifier as `startTransactionRid` and the end transaction's resource identifier as `endTransactionRid`.
This will retrieve the content for the most recent version of the file since the `startTransactionRid` up to the 
`endTransactionRid`. Note that an intermediate snapshot transaction will remove all files from the view. Behavior
is undefined when the start and end transactions do not belong to the same root-to-leaf path.

To **get a file's content from a specific transaction** specify the Transaction's resource identifier as both the 
`startTransactionRid` and `endTransactionRid`.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-read`.

**operationId:** v1.getFileContent

**path:** /api/v1/datasets/{datasetRid}/files/{filePath}/content

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

**name:** body

##### Format

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
