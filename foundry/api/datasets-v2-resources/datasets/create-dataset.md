---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/datasets/create-dataset/"
title: "Create Dataset \u2022 API Reference"
---
# Create Dataset

## Endpoint

Creates a new Dataset. A default branch - `master` for most enrollments - will be created on the Dataset.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-write`.

**operationId:** v2.createDataset

**path:** /api/v2/datasets

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
| parentFolderRid | stringType | True | The unique resource identifier (RID) of a Folder. |
| name | stringType | True |  |

**example:** {"parentFolderRid":"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791","name":"My Dataset"}

### Response

#### Body

The created Dataset

**name:** Dataset

**example:** {"parentFolderRid":"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791","name":"My Dataset","rid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The Resource Identifier (RID) of a Dataset. |
| name | stringType | True |  |
| parentFolderRid | stringType | True | The unique resource identifier (RID) of a Folder. |

**example:** {"parentFolderRid":"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791","name":"My Dataset","rid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da"}

### Error Responses

| name | description |
| --- | --- |
| ResourceNameAlreadyExists | The provided resource name is already in use by another resource in the same folder. |
| CreateDatasetPermissionDenied | The provided token does not have permission to create a dataset in this folder. |
| TransactionNotCommitted | The given transaction has not been committed. |
| TransactionNotFound | The requested transaction could not be found on the dataset, or the client token does not have access to it. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
| CreateBranchPermissionDenied | The provided token does not have permission to create a branch of this dataset. |
| BranchAlreadyExists | The branch cannot be created because a branch with that name already exists. |
| InvalidBranchName | The requested branch name cannot be used. Branch names cannot be empty and must not look like RIDs or UUIDs. |
| InvalidDisplayName | The display name of a Resource should not be exactly `.` or `..`, contain a forward slash `/` and must be less than or equal to 700 characters. |
| FolderNotFound | The given Folder could not be found. |
