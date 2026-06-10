---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/resource-roles/remove-resource-roles/"
title: "Remove Resource Roles \u2022 API Reference"
---
# Remove Resource Roles

## Endpoint

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-write`.

**operationId:** v2.removeResourceRoles

**path:** /api/v2/filesystem/resources/{resourceRid}/roles/remove

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

**name:** RemoveResourceRolesRequest

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
| RemoveResourceRolesPermissionDenied | Could not remove the ResourceRole. |
| ResourceNotFound | The given Resource could not be found. |
