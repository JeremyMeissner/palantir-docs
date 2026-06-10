---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/project-resource-references/list-project-resource-references/"
title: "List Project Resource References \u2022 API Reference"
---
# List Project Resource References

## Endpoint

List all references in the given project

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-read`.

**operationId:** v2.listProjectResourceReferences

**path:** /api/v2/filesystem/projects/{projectRid}/references

### Operation Type

### Scopes

| name |
| --- |
| api:filesystem-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| projectRid | stringType | True | The unique resource identifier (RID) of a Project. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| referenceType | enumType | False | Filter references by type. If not provided, all references are returned. |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

### Response

#### Body

**name:** ListProjectResourceReferencesResponse

**example:** {"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| ProjectNotFound | The given Project could not be found. |
