---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-resources/files/upload-file/"
title: "Upload File \u2022 API Reference"
---
# Upload File

## Endpoint

Uploads a File to an existing Dataset.
The body of the request must contain the binary content of the file and the `Content-Type` header must be `application/octet-stream`.

By default the file is uploaded to a new transaction on the default branch - `master` for most enrollments.
If the file already exists only the most recent version will be visible in the updated view.

#### Advanced Usage

See [Datasets Core Concepts](/docs/foundry/data-integration/datasets/) for details on using branches and transactions. 

To **upload a file to a specific Branch** specify the Branch's identifier as `branchId`. A new transaction will 
be created and committed on this branch. By default the TransactionType will be `UPDATE`, to override this
default specify `transactionType` in addition to `branchId`. 
See [createBranch](/docs/foundry/api/datasets-resources/branches/create-branch/) to create a custom branch.

To **upload a file on a manually opened transaction** specify the Transaction's resource identifier as
`transactionRid`. This is useful for uploading multiple files in a single transaction. 
See [createTransaction](/docs/foundry/api/datasets-resources/transactions/create-transaction/) to open a transaction.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-write`.

**operationId:** v1.uploadFile

**path:** /api/v1/datasets/{datasetRid}/files:upload

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of the Dataset on which to upload the File. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| filePath | stringType | True | The File's path within the Dataset. |
| branchId | stringType | False | The identifier (name) of the Branch on which to upload the File. Defaults to `master` for most enrollments. |
| transactionType | enumType | False | The type of the Transaction to create when using branchId. Defaults to `UPDATE`. |
| transactionRid | stringType | False | The Resource Identifier (RID) of the open Transaction on which to upload the File. |

### Request

#### Body

**name:** body

##### Format

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
| InvalidFilePath | The provided file path is not valid. |
| UploadFilePermissionDenied | The provided token does not have permission to upload the given file to the given dataset and transaction. |
| OpenTransactionAlreadyExists | A transaction is already open on this dataset and branch. A branch of a dataset can only have one open transaction at a time. |
| CreateTransactionPermissionDenied | The provided token does not have permission to create a transaction on this dataset. |
| FileAlreadyExists | The given file path already exists in the dataset and transaction. |
| InvalidBranchId | The requested branch name cannot be used. Branch names cannot be empty and must not look like RIDs or UUIDs. |
| BranchNotFound | The requested branch could not be found, or the client token does not have access to it. |
| AbortTransactionPermissionDenied | The provided token does not have permission to abort the given transaction on the given dataset. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
| TransactionNotFound | The requested transaction could not be found on the dataset, or the client token does not have access to it. |
| CommitTransactionPermissionDenied | The provided token does not have permission to commit the given transaction on the given dataset. |
| TransactionNotOpen | The given transaction is not open. |
