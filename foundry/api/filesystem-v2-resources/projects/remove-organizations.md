---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/projects/remove-organizations/"
title: "Remove Organizations \u2022 API Reference"
---
# Remove Organizations

## Endpoint

Removes Organizations from a Project.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-write`.

**operationId:** v2.removeOrganizations

**path:** /api/v2/filesystem/projects/{projectRid}/removeOrganizations

### Operation Type

### Scopes

| name |
| --- |
| api:filesystem-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| projectRid | stringType | True | The unique resource identifier (RID) of a Project. |

### Request

#### Body

**name:** RemoveOrganizationsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| organizationRids | listType | False |  |

**example:** {"organizationRids":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"]}

### Error Responses

| name | description |
| --- | --- |
| OrganizationsNotFound | At least one organization RID could not be found. |
| OrganizationCannotBeRemoved | An organization cannot be removed from a project if it would result in a project with no organizations under a space marked with an organization. |
| InvalidOrganizationHierarchy | Organizations on a project must also exist on the parent space. This error is thrown if the configuration  of a project's organizations (on creation or subsequently) results in the project being marked with either  no organizations in a marked space, or with an organization that is not present on the parent space. |
| RemoveOrganizationsPermissionDenied | Could not removeOrganizations the Project. |
| ProjectNotFound | The given Project could not be found. |
