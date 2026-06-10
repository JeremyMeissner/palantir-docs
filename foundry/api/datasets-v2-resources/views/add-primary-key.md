---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/views/add-primary-key/"
title: "Add Primary Key \u2022 API Reference"
---
# Add Primary Key

## Endpoint

Adds a primary key to a View that does not already have one. Primary keys are treated as 
guarantees provided by the creator of the dataset.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-write`.

**operationId:** v2.addPrimaryKey

**path:** /api/v2/datasets/views/{viewDatasetRid}/addPrimaryKey

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

**name:** AddPrimaryKeyRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| branch | stringType | False | The name of a Branch. |
| primaryKey | objectType | True | The primary key of the dataset. Primary keys are treated as guarantees provided by the creator of the dataset. |

**example:** {"branch":"master","primaryKey":{"columns":["colA"],"resolution":{"type":"duplicate","deletionColumn":"deletionCol","resolutionStrategy":{"type":"latestWins","columns":["colB","colC"]}}}}

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
| ViewPrimaryKeyCannotBeModified | A primary key already exits. |
| ViewNotFound | The requested View could not be found. Either the view does not exist, the branch is not valid or the client token does not have access to it. |
| ViewPrimaryKeyMustContainAtLeastOneColumn | No columns were provided as part of the primary key |
| ViewPrimaryKeyRequiresBackingDatasets | Cannot add a primary key to a View that does not have any backing datasets. |
| InvalidViewPrimaryKeyColumnType | The type of each referenced column in the primary key must be one of the following: BYTE, SHORT, DECIMAL, INTEGER, LONG, STRING, BOOLEAN, TIMESTAMP or DATE. |
| NotAllColumnsInPrimaryKeyArePresent | Not all columns in the View's primary key are present in the dataset(s). |
| ViewPrimaryKeyDeletionColumnNotInDatasetSchema | The deletion column is not present in the dataset. |
| InvalidViewPrimaryKeyDeletionColumn | The deletion column must be a boolean. |
| AddPrimaryKeyPermissionDenied | Could not addPrimaryKey the View. |
