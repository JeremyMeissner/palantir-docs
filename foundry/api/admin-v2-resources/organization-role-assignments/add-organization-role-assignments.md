---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/organization-role-assignments/add-organization-role-assignments/"
title: "Add Organization Role Assignments \u2022 API Reference"
---
# Add Organization Role Assignments

## Endpoint

Assign roles to principals for the given Organization. At most 100 role assignments can be added in a single request.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.addOrganizationRoleAssignments

**path:** /api/v2/admin/organizations/{organizationRid}/roleAssignments/add

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

**name:** AddOrganizationRoleAssignmentsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| roleAssignments | listType | False |  |

**example:** {"roleAssignments":[{"roleId":"8bf49052-dc37-4528-8bf0-b551cfb71268","principalId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de"}]}

### Error Responses

| name | description |
| --- | --- |
| PrincipalNotFound | A principal (User or Group) with the given PrincipalId could not be found |
| AddOrganizationRoleAssignmentsPermissionDenied | Could not add the OrganizationRoleAssignment. |
| OrganizationNotFound | The given Organization could not be found. |
