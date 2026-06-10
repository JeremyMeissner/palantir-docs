---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-resources/datasets/get-dataset/"
title: "Get Dataset \u2022 API Reference"
---
# Get Dataset

## Endpoint

Gets the Dataset with the given DatasetRid.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-read`.

**operationId:** v1.getDataset

**path:** /api/v1/datasets/{datasetRid}

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

**example:** {"rid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","name":"My Dataset","parentFolderRid":"ri.foundry.main.folder.bfe58487-4c56-4c58-aba7-25defd6163c4"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The Resource Identifier (RID) of a Dataset. |
| name | stringType | True |  |
| parentFolderRid | stringType | True |  |

**example:** {"rid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","name":"My Dataset","parentFolderRid":"ri.foundry.main.folder.bfe58487-4c56-4c58-aba7-25defd6163c4"}

### Error Responses

| name | description |
| --- | --- |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
