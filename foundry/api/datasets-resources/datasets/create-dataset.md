---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-resources/datasets/create-dataset/"
title: "Create Dataset \u2022 API Reference"
---
# Create Dataset

## Endpoint

Creates a new Dataset. A default branch - `master` for most enrollments - will be created on the Dataset.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-write`.

**operationId:** v1.createDataset

**path:** /api/v1/datasets

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-write |

### Request

#### Body

**name:** CreateDatasetRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| name | stringType | True |  |
| parentFolderRid | stringType | True |  |

**example:** {"name":"My Dataset","parentFolderRid":"ri.foundry.main.folder.bfe58487-4c56-4c58-aba7-25defd6163c4"}

### Response

#### Body

**name:** Dataset

**example:** {"rid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","path":"/Empyrean Airlines/My Important Project/My Dataset"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The Resource Identifier (RID) of a Dataset. |
| name | stringType | True |  |
| parentFolderRid | stringType | True |  |

**example:** {"rid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","path":"/Empyrean Airlines/My Important Project/My Dataset"}

### Error Responses

| name | description |
| --- | --- |
| InvalidBranchId | The requested branch name cannot be used. Branch names cannot be empty and must not look like RIDs or UUIDs. |
| TransactionNotCommitted | The given transaction has not been committed. |
| TransactionNotFound | The requested transaction could not be found on the dataset, or the client token does not have access to it. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
| CreateBranchPermissionDenied | The provided token does not have permission to create a branch of this dataset. |
| BranchAlreadyExists | The branch cannot be created because a branch with that name already exists. |
| ResourceNameAlreadyExists | The provided resource name is already in use by another resource in the same folder. |
| FolderNotFound | The requested folder could not be found, or the client token does not have access to it. |
| CreateDatasetPermissionDenied | The provided token does not have permission to create a dataset in this folder. |
