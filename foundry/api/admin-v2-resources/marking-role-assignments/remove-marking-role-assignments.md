---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/marking-role-assignments/remove-marking-role-assignments/"
title: "Remove Marking Role Assignments \u2022 API Reference"
---
# Remove Marking Role Assignments

## Endpoint

Removes role assignments for the given Marking. For Organization markings, only the USE and DECLASSIFY
roles are supported; the ADMINISTER role must be managed via the Organization Role Assignment endpoints.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.removeMarkingRoleAssignments

**path:** /api/v2/admin/markings/{markingId}/roleAssignments/remove

### Operation Type

### Scopes

| name |
| --- |
| api:admin-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| markingId | stringType | True | The ID of a security marking. |

### Request

#### Body

**name:** RemoveMarkingRoleAssignmentsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| roleAssignments | listType | False |  |

**example:** {"roleAssignments":[{"role":"ADMINISTER","principalId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de"}]}

### Error Responses

| name | description |
| --- | --- |
| RemoveMarkingRoleAssignmentsRemoveAllAdministratorsNotAllowed | You cannot remove all administrators from a marking. |
| PrincipalNotFound | A principal (User or Group) with the given PrincipalId could not be found |
| GetMarkingPermissionDenied | The provided token does not have permission to view the marking. |
| ListMarkingRoleAssignmentsPermissionDenied | The provided token does not have permission to list assigned roles for this marking. |
| OrganizationMarkingAdministerRoleNotSupported | The ADMINISTER role on Organization markings cannot be managed through the Marking Role Assignments endpoints. To manage administrator roles for an Organization, use the Organization Role Assignment endpoints instead. |
| RemoveMarkingRoleAssignmentsPermissionDenied | Could not remove the MarkingRoleAssignment. |
| MarkingNotFound | The given Marking could not be found. |
| RemoveMarkingMembersPermissionDenied | Could not remove the MarkingMember. |
