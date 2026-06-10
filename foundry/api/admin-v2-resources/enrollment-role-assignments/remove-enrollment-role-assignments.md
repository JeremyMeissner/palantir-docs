---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/enrollment-role-assignments/remove-enrollment-role-assignments/"
title: "Remove Enrollment Role Assignments \u2022 API Reference"
---
# Remove Enrollment Role Assignments

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Remove roles from principals for the given Enrollment. At most 100 role assignments can be removed in a single request.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.removeEnrollmentRoleAssignments

**path:** /api/v2/admin/enrollments/{enrollmentRid}/roleAssignments/remove

### Operation Type

### Scopes

| name |
| --- |
| api:admin-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| enrollmentRid | stringType | True |  |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** RemoveEnrollmentRoleAssignmentsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| roleAssignments | listType | False |  |

**example:** {"roleAssignments":[{"roleId":"8bf49052-dc37-4528-8bf0-b551cfb71268","principalId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de"}]}

### Error Responses

| name | description |
| --- | --- |
| PrincipalNotFound | A principal (User or Group) with the given PrincipalId could not be found |
| EnrollmentRoleNotFound | One of the provided role IDs was not found. |
| RemoveEnrollmentRoleAssignmentsPermissionDenied | Could not remove the EnrollmentRoleAssignment. |
| EnrollmentNotFound | The given Enrollment could not be found. |
