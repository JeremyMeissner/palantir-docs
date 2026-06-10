---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/marking-role-assignments/list-marking-role-assignments/"
title: "List Marking Role Assignments \u2022 API Reference"
---
# List Marking Role Assignments

## Endpoint

List all principals who are assigned a role for the given Marking. Ignores the `pageSize` parameter.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.listMarkingRoleAssignments

**path:** /api/v2/admin/markings/{markingId}/roleAssignments

### Operation Type

### Scopes

| name |
| --- |
| api:admin-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| markingId | stringType | True | The ID of a security marking. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

### Response

#### Body

**name:** ListMarkingRoleAssignmentsResponse

**example:** {"data":[{"role":"ADMINISTER","principalId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","principalType":"USER"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"role":"ADMINISTER","principalId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","principalType":"USER"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| ListMarkingRoleAssignmentsPermissionDenied | The provided token does not have permission to list assigned roles for this marking. |
| MarkingNotFound | The given Marking could not be found. |
