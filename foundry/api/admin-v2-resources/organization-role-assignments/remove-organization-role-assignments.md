---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/organization-role-assignments/remove-organization-role-assignments/"
title: "Remove Organization Role Assignments \u2022 API Reference"
---
# Remove Organization Role Assignments

## Endpoint

Remove roles from principals for the given Organization. At most 100 role assignments can be removed in a single request.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.removeOrganizationRoleAssignments

**path:** /api/v2/admin/organizations/{organizationRid}/roleAssignments/remove

### Operation Type

### Scopes

| name |
| --- |
| api:admin-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| organizationRid | stringType | True |  |

### Request

#### Body

**name:** RemoveOrganizationRoleAssignmentsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| roleAssignments | listType | False |  |

**example:** {"roleAssignments":[{"roleId":"8bf49052-dc37-4528-8bf0-b551cfb71268","principalId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de"}]}

### Error Responses

| name | description |
| --- | --- |
| PrincipalNotFound | A principal (User or Group) with the given PrincipalId could not be found |
| RemoveOrganizationRoleAssignmentsPermissionDenied | Could not remove the OrganizationRoleAssignment. |
| OrganizationNotFound | The given Organization could not be found. |
