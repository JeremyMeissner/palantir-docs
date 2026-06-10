---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/datasets/get-dataset/"
title: "Get Dataset \u2022 API Reference"
---
# Get Dataset

## Endpoint

Get the Dataset with the specified rid.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-read`.

**operationId:** v2.getDataset

**path:** /api/v2/datasets/{datasetRid}

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of a Dataset. |

### Response

#### Body

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
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
