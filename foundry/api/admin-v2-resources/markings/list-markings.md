---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/markings/list-markings/"
title: "List Markings \u2022 API Reference"
---
# List Markings

## Endpoint

Maximum page size 100.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.listMarkings

**path:** /api/v2/admin/markings

### Operation Type

### Scopes

| name |
| --- |
| api:admin-read |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

### Response

#### Body

**name:** ListMarkingsResponse

**example:** {"data":[{"createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","organization":"ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa","name":"PII","description":"Contains personally identifiable information about our customers","createdTime":"2003-05-06T12:34:56.789Z","id":"18212f9a-0e63-4b79-96a0-aae04df23336","categoryId":"0950264e-01c8-4e83-81a9-1a6b7f77621a"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","organization":"ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa","name":"PII","description":"Contains personally identifiable information about our customers","createdTime":"2003-05-06T12:34:56.789Z","id":"18212f9a-0e63-4b79-96a0-aae04df23336","categoryId":"0950264e-01c8-4e83-81a9-1a6b7f77621a"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| InvalidPageSize | The provided page size was zero or negative. Page sizes must be greater than zero. |
