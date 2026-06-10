---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/projects/create-project/"
title: "Create Project \u2022 API Reference"
---
# Create Project

## Endpoint

Creates a new Project.

Note that third-party applications using this endpoint via OAuth2 cannot be associated with an
Ontology SDK as this will reduce the scope of operations to only those within specified projects.
When creating the application, select "No, I won't use an Ontology SDK" on the Resources page.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-write`.

**operationId:** v2.createProject

**path:** /api/v2/filesystem/projects/create

### Operation Type

### Scopes

| name |
| --- |
| api:filesystem-write |

### Request

#### Body

**name:** CreateProjectRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| displayName | stringType | True | The display name of the Resource |
| description | stringType | False |  |
| spaceRid | stringType | True | The unique resource identifier (RID) of a Space. |
| roleGrants | mapType | False |  |
| defaultRoles | listType | False |  |
| organizationRids | listType | False |  |
| resourceLevelRoleGrantsAllowed | booleanType | False | Whether role grants should be allowed on individual resources within the Project. When not specified, defaults to true. |

**example:** {"organizationRids":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"displayName":"My Important Project","defaultRoles":["8bf49052-dc37-4528-8bf0-b551cfb71268"],"description":"project description","roleGrants":{"8bf49052-dc37-4528-8bf0-b551cfb71268":[{"principalId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","principalType":"GROUP"}]},"spaceRid":"ri.compass.main.folder.a86ad5f5-3db5-48e4-9fdd-00aa3e5731ca"}

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
| ProjectCreationNotSupported | Project creation is not supported in the current user's space. |
| ProjectNameAlreadyExists | The requested display name for the created project is already being used in the space. |
| InvalidDisplayName | The display name of a Resource should not be exactly `.` or `..`, contain a forward slash `/` and must be less than or equal to 700 characters. |
| OrganizationsNotFound | At least one organization RID could not be found. |
| InvalidRoleIds | A roleId referenced in either default roles or role grants does not exist in the project role set for the space. |
| CreateProjectNoOwnerLikeRoleGrant | The create project request would create a project with no principal being granted an owner-like role. As a result, there would be no user with administrative privileges over the project. A role is defined to be owner-like if it has the `compass:edit-project` operation. In the common case of the default role-set, this is just the `compass:manage` role. |
| OrganizationMarkingNotOnSpace | At least one of the organization markings associated with a passed organization is not applied on the requested space. |
| CreateProjectPermissionDenied | Could not create the Project. |
| ProjectNotFound | The given Project could not be found. |
| SpaceNotFound | The given Space could not be found. |
