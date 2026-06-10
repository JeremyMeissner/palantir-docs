---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/resources/get-by-path-resources-batch/"
title: "Get By Path Resources Batch \u2022 API Reference"
---
# Get By Path Resources Batch

## Endpoint

Gets multiple Resources by their absolute paths.
Returns a list of resources. If a path does not exist, is inaccessible, or refers to 
a root folder or space, it will not be included in the response.
At most 1,000 paths should be requested at once.

The maximum batch size for this endpoint is 1000.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-read`.

**operationId:** v2.getByPathResourcesBatch

**path:** /api/v2/filesystem/resources/getByPathBatch

### Operation Type

### Scopes

| name |
| --- |
| api:filesystem-read |

### Request

#### Body

**name:** body

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| GetByPathResourcesBatchRequestElement | objectType | True |  |

**example:** [{"path":"/My Organization-abcd/My Important Project/My Dataset"}]

### Response

#### Body

**name:** GetByPathResourcesBatchResponse

**example:** {"data":[{"projectRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","updatedTime":"2024-09-25T17:29:35.974Z","updatedBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","displayName":"My Dataset","description":"This dataset contains important data about Empyrean Airlines","rid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","type":"FOUNDRY_DATASET","spaceRid":"ri.compass.main.folder.a86ad5f5-3db5-48e4-9fdd-00aa3e5731ca","trashStatus":"NOT_TRASHED","parentFolderRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","path":"/Empyrean Airlines/My Important Project/My Dataset","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","createdTime":"2024-09-25T17:29:35.974Z"}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |

**example:** {"data":[{"projectRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","updatedTime":"2024-09-25T17:29:35.974Z","updatedBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","displayName":"My Dataset","description":"This dataset contains important data about Empyrean Airlines","rid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","type":"FOUNDRY_DATASET","spaceRid":"ri.compass.main.folder.a86ad5f5-3db5-48e4-9fdd-00aa3e5731ca","trashStatus":"NOT_TRASHED","parentFolderRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","path":"/Empyrean Airlines/My Important Project/My Dataset","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","createdTime":"2024-09-25T17:29:35.974Z"}]}
