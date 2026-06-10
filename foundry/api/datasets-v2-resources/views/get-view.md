---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/views/get-view/"
title: "Get View \u2022 API Reference"
---
# Get View

## Endpoint

Get metadata for a View.

**operationId:** v2.getView

**path:** /api/v2/datasets/views/{viewDatasetRid}

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| viewDatasetRid | stringType | True | The rid of the View. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branch | stringType | False | The name of a Branch. |

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
| ViewNotFound | The requested View could not be found. Either the view does not exist, the branch is not valid or the client token does not have access to it. |
