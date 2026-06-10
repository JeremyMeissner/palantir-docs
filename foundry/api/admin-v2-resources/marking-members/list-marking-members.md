---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/marking-members/list-marking-members/"
title: "List Marking Members \u2022 API Reference"
---
# List Marking Members

## Endpoint

Lists all principals who can view resources protected by the given Marking. Ignores the `pageSize` parameter.
Requires `api:admin-write` because only marking administrators can view marking members.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.listMarkingMembers

**path:** /api/v2/admin/markings/{markingId}/markingMembers

### Operation Type

### Scopes

| name |
| --- |
| api:admin-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| markingId | stringType | True | The ID of a security marking. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| transitive | booleanType | False | When true, includes the transitive members of groups contained within groups that are members of this  Marking. For example, say the Marking has member Group A, and Group A has member User B. If  `transitive=false` only Group A will be returned, but if `transitive=true` then Group A and User B  will be returned. This will recursively resolve Groups through all layers of nesting.  Defaults to false. |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

### Response

#### Body

**name:** ListMarkingMembersResponse

**example:** {"data":[{"principalId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","principalType":"USER"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"principalId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","principalType":"USER"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| ListMarkingMembersPermissionDenied | The provided token does not have permission to list the members of this marking. |
| GetMarkingPermissionDenied | The provided token does not have permission to view the marking. |
| MarkingNotFound | The given Marking could not be found. |
