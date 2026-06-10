---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/projects/get-project/"
title: "Get Project \u2022 API Reference"
---
# Get Project

## Endpoint

Get the Project with the specified rid.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-read`.

**operationId:** v2.getProject

**path:** /api/v2/filesystem/projects/{projectRid}

### Operation Type

### Scopes

| name |
| --- |
| api:filesystem-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| projectRid | stringType | True | The unique resource identifier (RID) of a Project. |

### Response

#### Body

**name:** Project

**example:** {"path":"/Empyrean Airlines/My Important Project","updatedTime":"2024-09-25T17:29:35.974Z","updatedBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","displayName":"My Important Project","documentation":"project documentation","resourceLevelRoleGrantsAllowed":true,"description":"project description","createdTime":"2024-09-25T17:29:35.974Z","rid":"ri.compass.main.folder.01a79a9d-e293-48db-a585-9ffe221536e8","spaceRid":"ri.compass.main.folder.a86ad5f5-3db5-48e4-9fdd-00aa3e5731ca","trashStatus":"NOT_TRASHED"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The unique resource identifier (RID) of a Project. |
| displayName | stringType | True | The display name of the Project. Must be unique and cannot contain a / |
| description | stringType | False | The description associated with the Project. |
| documentation | stringType | False | The documentation associated with the Project. |
| path | stringType | True | The full path to the resource, including the resource name itself |
| createdBy | stringType | True | The Foundry user who created this resource |
| updatedBy | stringType | True | The Foundry user who last updated this resource |
| createdTime | stringType | True | The time at which the resource was created. |
| updatedTime | stringType | True | The time at which the resource was most recently updated. |
| trashStatus | enumType | True | The trash status of the Project. |
| spaceRid | stringType | True | The Space Resource Identifier (RID) that the Project lives in. |
| resourceLevelRoleGrantsAllowed | booleanType | True | Whether role grants are allowed on individual resources within the Project. |

**example:** {"path":"/Empyrean Airlines/My Important Project","updatedTime":"2024-09-25T17:29:35.974Z","updatedBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","displayName":"My Important Project","documentation":"project documentation","resourceLevelRoleGrantsAllowed":true,"description":"project description","createdTime":"2024-09-25T17:29:35.974Z","rid":"ri.compass.main.folder.01a79a9d-e293-48db-a585-9ffe221536e8","spaceRid":"ri.compass.main.folder.a86ad5f5-3db5-48e4-9fdd-00aa3e5731ca","trashStatus":"NOT_TRASHED"}

### Error Responses

| name | description |
| --- | --- |
| ProjectNotFound | The given Project could not be found. |
