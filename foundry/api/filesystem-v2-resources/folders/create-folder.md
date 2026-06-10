---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/folders/create-folder/"
title: "Create Folder \u2022 API Reference"
---
# Create Folder

## Endpoint

Creates a new Folder.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-write`.

**operationId:** v2.createFolder

**path:** /api/v2/filesystem/folders

### Operation Type

### Scopes

| name |
| --- |
| api:filesystem-write |

### Request

#### Body

**name:** CreateFolderRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| parentFolderRid | stringType | True | The parent folder Resource Identifier (RID). For Projects, this will be the Space RID and for Spaces, this value will be the root folder (`ri.compass.main.folder.0`). |
| displayName | stringType | True | The display name of the Resource |

**example:** {"parentFolderRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","displayName":"My Folder"}

### Response

#### Body

The created Folder

**name:** Folder

**example:** {"projectRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","updatedTime":"2024-09-25T17:29:35.974Z","updatedBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","displayName":"My Folder","description":"This dataset contains important data about Empyrean Airlines","rid":"ri.compass.main.folder.01a79a9d-e293-48db-a585-9ffe221536e8","type":"FOLDER","spaceRid":"ri.compass.main.folder.a86ad5f5-3db5-48e4-9fdd-00aa3e5731ca","trashStatus":"NOT_TRASHED","parentFolderRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","path":"/Empyrean Airlines/My Important Project/My Folder","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","createdTime":"2024-09-25T17:29:35.974Z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The unique resource identifier (RID) of a Folder. |
| displayName | stringType | True | The display name of the Resource |
| description | stringType | False | The description associated with the Folder. |
| documentation | stringType | False | The documentation associated with the Folder. |
| path | stringType | True | The full path to the resource, including the resource name itself |
| type | enumType | True | A folder can be a regular Folder, a [Project](/docs/foundry/getting-started/projects-and-resources/#projects) or a [Space](/docs/foundry/security/orgs-and-spaces/#spaces). |
| createdBy | stringType | True | The Foundry user who created this resource |
| updatedBy | stringType | True | The Foundry user who last updated this resource |
| createdTime | stringType | True | The time at which the resource was created. |
| updatedTime | stringType | True | The time at which the resource was most recently updated. |
| trashStatus | enumType | True | The trash status of the Folder. If trashed, this could either be because the Folder itself has been trashed or because one of its ancestors has been trashed. |
| parentFolderRid | stringType | True | The parent folder Resource Identifier (RID). For Projects, this will be the Space RID and for Spaces, this value will be the root folder (`ri.compass.main.folder.0`). |
| projectRid | stringType | False | The Project Resource Identifier (RID) that the Folder lives in. If the Folder is a Space, this value will not be defined. |
| spaceRid | stringType | True | The Space Resource Identifier (RID) that the Folder lives in. If the Folder is a Space, this value will be the same as the Folder RID. |

**example:** {"projectRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","updatedTime":"2024-09-25T17:29:35.974Z","updatedBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","displayName":"My Folder","description":"This dataset contains important data about Empyrean Airlines","rid":"ri.compass.main.folder.01a79a9d-e293-48db-a585-9ffe221536e8","type":"FOLDER","spaceRid":"ri.compass.main.folder.a86ad5f5-3db5-48e4-9fdd-00aa3e5731ca","trashStatus":"NOT_TRASHED","parentFolderRid":"ri.compass.main.folder.4cae7c13-b59f-48f6-9ef2-dbde603e4e33","path":"/Empyrean Airlines/My Important Project/My Folder","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","createdTime":"2024-09-25T17:29:35.974Z"}

### Error Responses

| name | description |
| --- | --- |
| ResourceNameAlreadyExists | The provided resource name is already in use by another resource in the same folder. |
| GetRootFolderNotSupported | Getting the root folder as a resource is not supported. |
| CreateFolderOutsideProjectNotSupported | The given Resource is not a folder. |
| InvalidFolder | The given Resource is not a Folder. |
| InvalidDisplayName | The display name of a Resource should not be exactly `.` or `..`, contain a forward slash `/` and must be less than or equal to 700 characters. |
| MissingDisplayName | A Display Name must be provided. |
| CreateFolderPermissionDenied | Could not create the Folder. |
| FolderNotFound | The given Folder could not be found. |
