---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/projects/create-project-from-template/"
title: "Create Project From Template \u2022 API Reference"
---
# Create Project From Template

## Endpoint

Creates a project from a project template.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-write`.

**operationId:** v2.createProjectFromTemplate

**path:** /api/v2/filesystem/projects/createFromTemplate

### Operation Type

### Scopes

| name |
| --- |
| api:filesystem-write |

### Request

#### Body

**name:** CreateProjectFromTemplateRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| templateRid | stringType | True | The unique resource identifier (RID) of a project template. |
| variableValues | mapType | False |  |
| defaultRoles | listType | False |  |
| organizationRids | listType | False |  |
| projectDescription | stringType | False |  |

**example:** {"variableValues":{"name":"my project name"},"organizationRids":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"defaultRoles":["8bf49052-dc37-4528-8bf0-b551cfb71268"],"templateRid":"ri.compass.main.template.c410f510-2937-420e-8ea3-8c9bcb3c1791"}

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
| ProjectTemplateNotFound | The project template RID referenced cannot be found. |
| DefaultRolesNotInSpaceRoleSet | The requested default roles are not in the role set of the space for the project template. |
| NotAuthorizedToApplyOrganization | The user is not authorized to apply at least one of the organization markings required to create the project from template. |
| InvalidOrganizationHierarchy | Organizations on a project must also exist on the parent space. This error is thrown if the configuration  of a project's organizations (on creation or subsequently) results in the project being marked with either  no organizations in a marked space, or with an organization that is not present on the parent space. |
| CreateProjectNoOwnerLikeRoleGrant | The create project request would create a project with no principal being granted an owner-like role. As a result, there would be no user with administrative privileges over the project. A role is defined to be owner-like if it has the `compass:edit-project` operation. In the common case of the default role-set, this is just the `compass:manage` role. |
| CreateGroupPermissionDenied | The user is not authorized to create the group in the organization required to create the project from template. |
| AddGroupToParentGroupPermissionDenied | The user is not authorized to add a a group to the parent group required to create the project from template. |
| TemplateGroupNameConflict | Creating the project from template would attempt to create new groups with names conflicting either with other new groups, or existing groups. |
| TemplateMarkingNameConflict | Creating the project from template would attempt to create new markings with names conflicting either with other new markings, or existing markings. |
| InvalidPrincipalIdsForGroupTemplate | The template requested for project creation contains principal IDs that do not exist. |
| InvalidDescription | Either the user has not passed a value for a template with unset project description, or has passed a value for a template with fixed project description. |
| InvalidOrganizations | Either the user has not passed organizations for a template with suggested organizations, or has passed organization for a template with fixed organizations. |
| MissingVariableValue | A variable defined on the template requested for project creation does not have a value set in the request. |
| InvalidVariable | A variable referenced in the request to create project from template is not defined on the template. |
| InvalidVariableEnumOption | The value passed in the request to create project from template for an enum type variable is not a valid option. |
| OrganizationsNotFound | At least one organization RID could not be found. |
| InvalidDefaultRoles | Either the user has not passed default roles for a template with suggested default roles, or has passed default roles for a template with fixed default roles. |
| CreateProjectFromTemplatePermissionDenied | Could not createFromTemplate the Project. |
| ProjectNotFound | The given Project could not be found. |
