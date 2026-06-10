---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/users/search-users/"
title: "Search Users \u2022 API Reference"
---
# Search Users

## Endpoint

Perform a case-insensitive prefix search for active users based on username, given name and family name.
Deleted users are not included in results. To list deleted users, use the `list` endpoint with `include=DELETED`.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.searchUsers

**path:** /api/v2/admin/users/search

### Operation Type

### Scopes

| name |
| --- |
| api:admin-read |

### Request

#### Body

**name:** SearchUsersRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| where | objectType | True |  |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"pageSize":100,"where":{"type":"queryString","value":"jsmith"},"pageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Response

#### Body

**name:** SearchUsersResponse

**example:** {"data":[{"givenName":"John","familyName":"Smith","organization":"ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa","realm":"palantir-internal-realm","attributes":{"multipass:givenName":["John"],"multipass:familyName":["Smith"],"multipass:email:primary":["jsmith@example.com"],"multipass:realm":["eab0a251-ca1a-4a84-a482-200edfb8026f"],"multipass:organization-rid":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"department":["Finance"],"jobTitle":["Accountant"]},"id":"0d1fe74e-2b70-4a93-9b1a-80070637788b","email":"jsmith@example.com","username":"jsmith","status":"ACTIVE"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"givenName":"John","familyName":"Smith","organization":"ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa","realm":"palantir-internal-realm","attributes":{"multipass:givenName":["John"],"multipass:familyName":["Smith"],"multipass:email:primary":["jsmith@example.com"],"multipass:realm":["eab0a251-ca1a-4a84-a482-200edfb8026f"],"multipass:organization-rid":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"department":["Finance"],"jobTitle":["Accountant"]},"id":"0d1fe74e-2b70-4a93-9b1a-80070637788b","email":"jsmith@example.com","username":"jsmith","status":"ACTIVE"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| InvalidPageSize | The provided page size was zero or negative. Page sizes must be greater than zero. |
| SearchUsersPermissionDenied | Could not search the User. |
