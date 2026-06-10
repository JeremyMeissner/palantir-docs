---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/group-memberships/list-group-memberships/"
title: "List Group Memberships \u2022 API Reference"
---
# List Group Memberships

## Endpoint

Lists all Groups a given User is a member of.

This is a paged endpoint. Each page may be smaller or larger than the requested page size. However, 
it is guaranteed that if there are more results available, the `nextPageToken` field will be populated. 
To get the next page, make the same request again, but set the value of the `pageToken` query parameter 
to be value of the `nextPageToken` value of the previous response. If there is no `nextPageToken` field 
in the response, you are on the last page.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.listGroupMemberships

**path:** /api/v2/admin/users/{userId}/groupMemberships

### Operation Type

### Scopes

| name |
| --- |
| api:admin-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| userId | stringType | True | A Foundry User ID. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| transitive | booleanType | False | When true, includes the transitive memberships of the Groups the User is a member of. For example, say the User is a member of Group A, and Group A is a member of Group B. If `transitive=false` only Group A will be returned, but if `transitive=true` then Groups A and B will be returned. This will recursively resolve Groups through all layers of nesting.  Defaults to false. |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

### Response

#### Body

**name:** ListGroupMembershipsResponse

**example:** {"data":[{"groupId":"0d1fe74e-2b70-4a93-9b1a-80070637788b"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"groupId":"0d1fe74e-2b70-4a93-9b1a-80070637788b"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| InvalidPageSize | The provided page size was zero or negative. Page sizes must be greater than zero. |
| UserDeleted | The user is deleted. |
| UserNotFound | The given User could not be found. |
