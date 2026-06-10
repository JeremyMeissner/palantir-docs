---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/group-members/list-group-members/"
title: "List Group Members \u2022 API Reference"
---
# List Group Members

## Endpoint

Lists all members (which can be a User or a Group) of a given Group.

This is a paged endpoint. Each page may be smaller or larger than the requested page size. However, 
it is guaranteed that if there are more results available, the `nextPageToken` field will be populated. 
To get the next page, make the same request again, but set the value of the `pageToken` query parameter 
to be value of the `nextPageToken` value of the previous response. If there is no `nextPageToken` field 
in the response, you are on the last page.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.listGroupMembers

**path:** /api/v2/admin/groups/{groupId}/groupMembers

### Operation Type

### Scopes

| name |
| --- |
| api:admin-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| groupId | stringType | True | A Foundry Group ID. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| transitive | booleanType | False | When true, includes the transitive members of groups contained within this group. For example, say the Group has member Group A, and Group A has member User B. If `transitive=false` only Group A will be returned, but if `transitive=true` then Group A and User B will be returned. This will recursively resolve Groups through all layers of nesting.  If `transitive` is true, `includeExpirations` cannot also be set to true.  Defaults to false. |
| includeExpirations | booleanType | False | When true, includes the expiration time of any temporary members of this group. `includeExpirations`  cannot be set to true if `transitive` is also set to true.  Defaults to false. |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

### Response

#### Body

**name:** ListGroupMembersResponse

**example:** {"data":[{"principalId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","expiration":"2026-01-31T00:00:00.000Z","principalType":"USER"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"principalId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","expiration":"2026-01-31T00:00:00.000Z","principalType":"USER"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| InvalidPageSize | The provided page size was zero or negative. Page sizes must be greater than zero. |
| ExpirationForTransitiveGroupMembersNotSupported | You cannot pass includeExpirations if transitive is true. |
| GroupNotFound | The given Group could not be found. |
