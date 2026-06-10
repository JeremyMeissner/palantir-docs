---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/organization-role-assignments/list-organization-role-assignments/"
title: "List Organization Role Assignments \u2022 API Reference"
---
# List Organization Role Assignments

## Endpoint

List all principals who are assigned a role for the given Organization.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.listOrganizationRoleAssignments

**path:** /api/v2/admin/organizations/{organizationRid}/roleAssignments

### Operation Type

### Scopes

| name |
| --- |
| api:admin-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| organizationRid | stringType | True |  |

### Response

#### Body

**name:** ListOrganizationRoleAssignmentsResponse

**example:** {"data":[{"roleId":"8bf49052-dc37-4528-8bf0-b551cfb71268","principalId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","principalType":"USER"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"roleId":"8bf49052-dc37-4528-8bf0-b551cfb71268","principalId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","principalType":"USER"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| ListOrganizationRoleAssignmentsPermissionDenied | The provided token does not have permission to list assigned roles for this organization. |
| OrganizationNotFound | The given Organization could not be found. |
