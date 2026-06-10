---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/files/upload-file/"
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
To **upload a file to a specific Branch** specify the Branch's name as `branchName`. A new transaction will 
be created and committed on this branch. By default the TransactionType will be `UPDATE`, to override this
default specify `transactionType` in addition to `branchName`. 
See [createBranch](/docs/foundry/api/datasets-resources/branches/create-branch/) to create a custom branch.
To **upload a file on a manually opened transaction** specify the Transaction's resource identifier as
`transactionRid`. This is useful for uploading multiple files in a single transaction. 
See [createTransaction](/docs/foundry/api/datasets-resources/transactions/create-transaction/) to open a transaction.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-write`.

**operationId:** v2.uploadFile

**path:** /api/v2/datasets/{datasetRid}/files/{filePath}/upload

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of a Dataset. |
| filePath | stringType | True | The path to a File within Foundry. Paths are relative and must not start with a leading slash. Examples: `my-file.txt`, `path/to/my-file.jpg`, `dataframe.snappy.parquet`. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branchName | stringType | False | The name of the Branch on which to upload the File. Defaults to `master` for most enrollments. |
| transactionType | enumType | False | The type of the Transaction to create when using branchName. Defaults to `UPDATE`. |
| transactionRid | stringType | False | The Resource Identifier (RID) of the open Transaction on which to upload the File. |

### Request

#### Body

**name:** body

##### Format

### Response

#### Body

**name:** File

**example:** {"path":"2020/09/30/trades.csv","updatedTime":"2020-09-30T12:34:56.789Z","transactionRid":"ri.foundry.main.transaction.0a0207cb-26b7-415b-bc80-66a3aa3933f4"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| path | stringType | True | The path to a File within Foundry. Paths are relative and must not start with a leading slash. Examples: `my-file.txt`, `path/to/my-file.jpg`, `dataframe.snappy.parquet`. |
| transactionRid | stringType | True | The Resource Identifier (RID) of a Transaction. |
| sizeBytes | stringType | False |  |
| updatedTime | stringType | True |  |

**example:** {"path":"2020/09/30/trades.csv","updatedTime":"2020-09-30T12:34:56.789Z","transactionRid":"ri.foundry.main.transaction.0a0207cb-26b7-415b-bc80-66a3aa3933f4"}

### Error Responses

| name | description |
| --- | --- |
| BranchNotFound | The requested branch could not be found, or the client token does not have access to it. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
| OpenTransactionAlreadyExists | A transaction is already open on this dataset and branch. A branch of a dataset can only have one open transaction at a time. |
| FileAlreadyExists | The given file path already exists in the dataset and transaction. |
| InvalidParameterCombination | The given parameters are individually valid but cannot be used in the given combination. |
| InvalidFilePath | The provided file path is invalid. Check that the path does not start with a leading slash. |
| TransactionNotFound | The requested transaction could not be found on the dataset, or the client token does not have access to it. |
| TransactionNotOpen | The given transaction is not open. |
| CreateTransactionPermissionDenied | The provided token does not have permission to create a transaction on this dataset. |
| AbortTransactionPermissionDenied | The provided token does not have permission to abort the given transaction on the given dataset. |
| CommitTransactionPermissionDenied | The provided token does not have permission to commit the given transaction on the given dataset. |
| InvalidBranchName | The requested branch name cannot be used. Branch names cannot be empty and must not look like RIDs or UUIDs. |
| UploadFilePermissionDenied | Could not upload the File. |
