---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/folders/get-folders-batch/"
title: "Get Folders Batch \u2022 API Reference"
---
# Get Folders Batch

## Endpoint

Fetches multiple folders in a single request.

The maximum batch size for this endpoint is 1000.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-read`.

**operationId:** v2.getFoldersBatch

**path:** /api/v2/filesystem/folders/getBatch

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
| GetFoldersBatchRequestElement | objectType | True |  |

**example:** [{"folderRid":"ri.compass.main.folder.01a79a9d-e293-48db-a585-9ffe221536e8"}]

### Response

#### Body

**name:** GetFoldersBatchResponse

**example:** {"data":{"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791":{"projectRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","updatedTime":"2024-09-25T17:29:35.974Z","updatedBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","displayName":"My Folder","description":"This dataset contains important data about Empyrean Airlines","rid":"ri.compass.main.folder.01a79a9d-e293-48db-a585-9ffe221536e8","type":"FOLDER","spaceRid":"ri.compass.main.folder.a86ad5f5-3db5-48e4-9fdd-00aa3e5731ca","trashStatus":"NOT_TRASHED","parentFolderRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","path":"/Empyrean Airlines/My Important Project/My Folder","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","createdTime":"2024-09-25T17:29:35.974Z"}}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | mapType | False |  |

**example:** {"data":{"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791":{"projectRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","updatedTime":"2024-09-25T17:29:35.974Z","updatedBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","displayName":"My Folder","description":"This dataset contains important data about Empyrean Airlines","rid":"ri.compass.main.folder.01a79a9d-e293-48db-a585-9ffe221536e8","type":"FOLDER","spaceRid":"ri.compass.main.folder.a86ad5f5-3db5-48e4-9fdd-00aa3e5731ca","trashStatus":"NOT_TRASHED","parentFolderRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","path":"/Empyrean Airlines/My Important Project/My Folder","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","createdTime":"2024-09-25T17:29:35.974Z"}}}
