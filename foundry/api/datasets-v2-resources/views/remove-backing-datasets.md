---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/views/remove-backing-datasets/"
title: "Remove Backing Datasets \u2022 API Reference"
---
# Remove Backing Datasets

## Endpoint

Removes specified backing datasets from a View. Removing a dataset triggers a 
[SNAPSHOT](/docs/foundry/data-integration/datasets#snapshot) transaction on the next update. If a 
specified dataset does not exist, no error is thrown.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-write`.

**operationId:** v2.removeBackingDatasets

**path:** /api/v2/datasets/views/{viewDatasetRid}/removeBackingDatasets

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| viewDatasetRid | stringType | True | The rid of the View. |

### Request

#### Body

**name:** RemoveBackingDatasetsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| branch | stringType | False | The name of a Branch. |
| backingDatasets | listType | False |  |

**example:** {"backingDatasets":[{"datasetRid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","stopPropagatingMarkingIds":["18212f9a-0e63-4b79-96a0-aae04df23336"],"branch":"master"}],"branch":"master"}

### Response

#### Body

**name:** View

**example:** {"datasetRid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","parentFolderRid":"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791","viewName":"My Dataset","backingDatasets":[{"datasetRid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","stopPropagatingMarkingIds":["18212f9a-0e63-4b79-96a0-aae04df23336"],"branch":"master"}],"branch":"master","primaryKey":{"columns":["order_id"]}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| viewName | stringType | True |  |
| datasetRid | stringType | True | The rid of the View. |
| parentFolderRid | stringType | True | The unique resource identifier (RID) of a Folder. |
| branch | stringType | False | The branch name of the View. If not specified, defaults to `master` for most enrollments. |
| backingDatasets | listType | False |  |
| primaryKey | objectType | False | The primary key of the dataset. Primary keys are treated as guarantees provided by the creator of the dataset. |

**example:** {"datasetRid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","parentFolderRid":"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791","viewName":"My Dataset","backingDatasets":[{"datasetRid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","stopPropagatingMarkingIds":["18212f9a-0e63-4b79-96a0-aae04df23336"],"branch":"master"}],"branch":"master","primaryKey":{"columns":["order_id"]}}

### Error Responses

| name | description |
| --- | --- |
| InvalidViewBackingDataset | Either you do not have access to one or more of the backing datasets or it does not exist. |
| ViewNotFound | The requested View could not be found. Either the view does not exist, the branch is not valid or the client token does not have access to it. |
| InputBackingDatasetNotInOutputViewProject | One or more backing datasets do not live in the same project as the view. Either move the input datasets to the same project as the view or add them as project references. |
| RemoveBackingDatasetsPermissionDenied | Could not removeBackingDatasets the View. |
