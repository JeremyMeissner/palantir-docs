---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/resource-roles/list-resource-roles/"
title: "List Resource Roles \u2022 API Reference"
---
# List Resource Roles

## Endpoint

List the roles on a resource.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-read`.

**operationId:** v2.listResourceRoles

**path:** /api/v2/filesystem/resources/{resourceRid}/roles

### Operation Type

### Scopes

| name |
| --- |
| api:filesystem-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| resourceRid | stringType | True | The unique resource identifier (RID) of a Resource. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| includeInherited | booleanType | False | Whether to include inherited roles on the resource. |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

### Response

#### Body

**name:** ListResourceRolesResponse

**example:** {"data":[{"resourceRolePrincipal":{"type":"principalWithId","principalId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","principalType":"GROUP"},"roleId":"8bf49052-dc37-4528-8bf0-b551cfb71268"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"resourceRolePrincipal":{"type":"principalWithId","principalId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","principalType":"GROUP"},"roleId":"8bf49052-dc37-4528-8bf0-b551cfb71268"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| ResourceNotFound | The given Resource could not be found. |
