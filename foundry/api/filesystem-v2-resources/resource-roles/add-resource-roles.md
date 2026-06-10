---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/resource-roles/add-resource-roles/"
title: "Add Resource Roles \u2022 API Reference"
---
# Add Resource Roles

## Endpoint

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-write`.

**operationId:** v2.addResourceRoles

**path:** /api/v2/filesystem/resources/{resourceRid}/roles/add

### Operation Type

### Scopes

| name |
| --- |
| api:filesystem-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| resourceRid | stringType | True | The unique resource identifier (RID) of a Resource. |

### Request

#### Body

**name:** AddResourceRolesRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| roles | listType | False |  |

**example:** {"roles":[{"resourceRolePrincipal":{"type":"principalIdOnly","principalId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de"},"roleId":"8bf49052-dc37-4528-8bf0-b551cfb71268"}]}

### Error Responses

| name | description |
| --- | --- |
| InvalidRoleIds | A roleId referenced in either default roles or role grants does not exist in the project role set for the space. |
| PrincipalNotFound | A principal (User or Group) with the given PrincipalId could not be found |
| AddResourceRolesPermissionDenied | Could not add the ResourceRole. |
| ResourceNotFound | The given Resource could not be found. |
