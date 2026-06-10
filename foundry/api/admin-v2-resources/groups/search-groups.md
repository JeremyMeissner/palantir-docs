---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/groups/search-groups/"
title: "Search Groups \u2022 API Reference"
---
# Search Groups

## Endpoint

Perform a case-insensitive prefix search for groups based on group name.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.searchGroups

**path:** /api/v2/admin/groups/search

### Operation Type

### Scopes

| name |
| --- |
| api:admin-read |

### Request

#### Body

**name:** SearchGroupsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| where | objectType | True |  |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"pageSize":100,"where":{"type":"queryString","value":"jsmith"},"pageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Response

#### Body

**name:** SearchGroupsResponse

**example:** {"data":[{"name":"Data Source Admins","organizations":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"description":"Create and modify data sources in the platform","realm":"palantir-internal-realm","attributes":{"multipass:realm":["eab0a251-ca1a-4a84-a482-200edfb8026f"],"multipass:organization-rid":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"]},"id":"0d1fe74e-2b70-4a93-9b1a-80070637788b"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"name":"Data Source Admins","organizations":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"description":"Create and modify data sources in the platform","realm":"palantir-internal-realm","attributes":{"multipass:realm":["eab0a251-ca1a-4a84-a482-200edfb8026f"],"multipass:organization-rid":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"]},"id":"0d1fe74e-2b70-4a93-9b1a-80070637788b"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| InvalidPageSize | The provided page size was zero or negative. Page sizes must be greater than zero. |
| SearchGroupsPermissionDenied | Could not search the Group. |
