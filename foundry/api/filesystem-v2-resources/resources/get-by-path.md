---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/resources/get-by-path/"
title: "Get By Path \u2022 API Reference"
---
# Get By Path

## Endpoint

Get a Resource by its absolute path.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-read`.

**operationId:** v2.getByPath

**path:** /api/v2/filesystem/resources/getByPath

### Operation Type

### Scopes

| name |
| --- |
| api:filesystem-read |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| path | stringType | True | The path to the Resource. The leading slash is optional. |

### Response

#### Body

**name:** Resource

**example:** {"projectRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","updatedTime":"2024-09-25T17:29:35.974Z","updatedBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","displayName":"My Dataset","description":"This dataset contains important data about Empyrean Airlines","rid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","type":"FOUNDRY_DATASET","spaceRid":"ri.compass.main.folder.a86ad5f5-3db5-48e4-9fdd-00aa3e5731ca","trashStatus":"NOT_TRASHED","parentFolderRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","path":"/Empyrean Airlines/My Important Project/My Dataset","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","createdTime":"2024-09-25T17:29:35.974Z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The unique resource identifier (RID) of a Resource. |
| displayName | stringType | True | The display name of the Resource |
| description | stringType | False | The description of the Resource |
| documentation | stringType | False | The documentation associated with the Resource |
| path | stringType | True | The full path to the resource, including the resource name itself |
| type | enumType | True | The type of the Resource derived from the Resource Identifier (RID). |
| createdBy | stringType | True | The user that created the Resource. |
| updatedBy | stringType | True | The user that last updated the Resource. |
| createdTime | stringType | True | The timestamp that the Resource was last created. |
| updatedTime | stringType | True | The timestamp that the Resource was last modified. For folders, this includes any of its descendants. For top level folders (spaces and projects), this is not updated by child updates for performance reasons. |
| trashStatus | enumType | True | The trash status of the Resource. If trashed, this could either be because the Resource itself has been trashed or because one of its ancestors has been trashed. |
| parentFolderRid | stringType | True | The parent folder Resource Identifier (RID). For projects, this will be the Space RID. |
| projectRid | stringType | True | The Project Resource Identifier (RID) that the Resource lives in. If the Resource itself is a Project, this value will still be populated with the Project RID. |
| spaceRid | stringType | True | The Space Resource Identifier (RID) that the Resource lives in. |

**example:** {"projectRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","updatedTime":"2024-09-25T17:29:35.974Z","updatedBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","displayName":"My Dataset","description":"This dataset contains important data about Empyrean Airlines","rid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","type":"FOUNDRY_DATASET","spaceRid":"ri.compass.main.folder.a86ad5f5-3db5-48e4-9fdd-00aa3e5731ca","trashStatus":"NOT_TRASHED","parentFolderRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","path":"/Empyrean Airlines/My Important Project/My Dataset","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","createdTime":"2024-09-25T17:29:35.974Z"}

### Error Responses

| name | description |
| --- | --- |
| PathNotFound | The given path could not be found. |
| GetRootFolderNotSupported | Getting the root folder as a resource is not supported. |
| GetSpaceResourceNotSupported | Getting a space as a resource is not supported. |
| InvalidPath | The given path is invalid.   A valid path has all components separated by a single `/`. |
| GetByPathPermissionDenied | Could not getByPath the Resource. |
| ResourceNotFound | The given Resource could not be found. |
