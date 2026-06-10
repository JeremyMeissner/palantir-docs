---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/views/create-view/"
title: "Create View \u2022 API Reference"
---
# Create View

## Endpoint

Create a new View.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-write`.

**operationId:** v2.createView

**path:** /api/v2/datasets/views

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-write |

### Request

#### Body

**name:** CreateViewRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| parentFolderRid | stringType | True | The unique resource identifier (RID) of a Folder. |
| viewName | stringType | True |  |
| backingDatasets | listType | False |  |
| branch | stringType | False | The branch name of the View. If not specified, defaults to `master` for most enrollments. |
| primaryKey | objectType | False | The primary key of the dataset. Primary keys are treated as guarantees provided by the creator of the dataset. |

**example:** {"parentFolderRid":"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791","viewName":"My Dataset","backingDatasets":[{"datasetRid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","stopPropagatingMarkingIds":["18212f9a-0e63-4b79-96a0-aae04df23336"],"branch":"master"}],"branch":"master","primaryKey":{"columns":["order_id"]}}

### Response

#### Body

The created View

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
| CreateDatasetPermissionDenied | The provided token does not have permission to create a dataset in this folder. |
| ViewNotFound | The requested View could not be found. Either the view does not exist, the branch is not valid or the client token does not have access to it. |
| InvalidViewBackingDataset | Either you do not have access to one or more of the backing datasets or it does not exist. |
| ViewPrimaryKeyMustContainAtLeastOneColumn | No columns were provided as part of the primary key |
| ViewPrimaryKeyRequiresBackingDatasets | Cannot add a primary key to a View that does not have any backing datasets. |
| ViewDatasetCleanupFailed | Failed to delete dataset following View creation failure. |
| ResourceNameAlreadyExists | The provided resource name is already in use by another resource in the same folder. |
| InputBackingDatasetNotInOutputViewProject | One or more backing datasets do not live in the same project as the view. Either move the input datasets to the same project as the view or add them as project references. |
| InvalidViewPrimaryKeyColumnType | The type of each referenced column in the primary key must be one of the following: BYTE, SHORT, DECIMAL, INTEGER, LONG, STRING, BOOLEAN, TIMESTAMP or DATE. |
| InvalidViewPrimaryKeyDeletionColumn | The deletion column must be a boolean. |
| ViewPrimaryKeyDeletionColumnNotInDatasetSchema | The deletion column is not present in the dataset. |
| NotAllColumnsInPrimaryKeyArePresent | Not all columns in the View's primary key are present in the dataset(s). |
| InvalidDisplayName | The display name of a Resource should not be exactly `.` or `..`, contain a forward slash `/` and must be less than or equal to 700 characters. |
| NotAuthorizedToDeclassifyMarkings | The caller does not have DECLASSIFY permission on these markings or the markings do not exist. |
| CreateViewPermissionDenied | Could not create the View. |
| FolderNotFound | The given Folder could not be found. |
