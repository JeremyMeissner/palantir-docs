---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/files/delete-file/"
title: "Delete File \u2022 API Reference"
---
# Delete File

## Endpoint

Deletes a File from a Dataset. By default the file is deleted in a new transaction on the default 
branch - `master` for most enrollments. The file will still be visible on historical views.
#### Advanced Usage
See [Datasets Core Concepts](/docs/foundry/data-integration/datasets/) for details on using branches and transactions.
To **delete a File from a specific Branch** specify the Branch's name as `branchName`. A new delete Transaction 
will be created and committed on this branch.
To **delete a File using a manually opened Transaction**, specify the Transaction's resource identifier 
as `transactionRid`. The transaction must be of type `DELETE`. This is useful for deleting multiple files in a
single transaction. See [createTransaction](/docs/foundry/api/datasets-resources/transactions/create-transaction/) to 
open a transaction.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-write`.

**operationId:** v2.deleteFile

**path:** /api/v2/datasets/{datasetRid}/files/{filePath}

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
| branchName | stringType | False | The name of the Branch on which to delete the File. Defaults to `master` for most enrollments. |
| transactionRid | stringType | False | The Resource Identifier (RID) of the open delete Transaction on which to delete the File. |

### Error Responses

| name | description |
| --- | --- |
| BranchNotFound | The requested branch could not be found, or the client token does not have access to it. |
| FileNotFoundOnBranch | The requested file could not be found on the given branch, or the client token does not have access to it. |
| OpenTransactionAlreadyExists | A transaction is already open on this dataset and branch. A branch of a dataset can only have one open transaction at a time. |
| InvalidParameterCombination | The given parameters are individually valid but cannot be used in the given combination. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
| TransactionNotFound | The requested transaction could not be found on the dataset, or the client token does not have access to it. |
| FileNotFoundOnTransactionRange | The requested file could not be found on the given transaction range, or the client token does not have access to it. |
| InvalidTransactionType | The given transaction type is not valid. Valid transaction types are `SNAPSHOT`, `UPDATE`, `APPEND`, and `DELETE`. |
| TransactionNotOpen | The given transaction is not open. |
| CreateTransactionPermissionDenied | The provided token does not have permission to create a transaction on this dataset. |
| AbortTransactionPermissionDenied | The provided token does not have permission to abort the given transaction on the given dataset. |
| CommitTransactionPermissionDenied | The provided token does not have permission to commit the given transaction on the given dataset. |
| InvalidBranchName | The requested branch name cannot be used. Branch names cannot be empty and must not look like RIDs or UUIDs. |
| DeleteFilePermissionDenied | Could not delete the File. |
