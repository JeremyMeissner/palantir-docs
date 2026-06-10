---
source_url: "https://www.palantir.com/docs/foundry/api/checkpoints-v2-resources/records/search-records/"
title: "Search Records \u2022 API Reference"
---
# Search Records

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Search for checkpoint records.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:checkpoints-read`.

**operationId:** v2.searchRecords

**path:** /api/v2/checkpoints/records/search

### Operation Type

### Scopes

| name |
| --- |
| api:checkpoints-read |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** SearchRecordsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| where | objectType | True | Request payload for searching checkpoint records. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| pageSize | integerType | False | The page size for the search request. If no value is provided, a default of `100` will be used. |
| sortDirection | enumType | False | Chronological order of creation time for records to be returned in. Defaults to reverse chronological order (DESC). |

**example:** {"sortDirection":"DESC","pageSize":100,"where":{"filter":{"type":"eq","field":"checkpointType","value":"CONTOUR_EXPORT"}},"pageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Response

#### Body

Response payload for searching checkpoint records.

**name:** SearchCheckpointRecordsResponse

**example:** {"data":[{"rid":"ri.checkpoints.main.checkpoint.a1b2c3d4-e5f6-7890-abcd-ef1234567890","type":"CONTOUR_EXPORT","scope":"USER_SCOPED","actingUser":{"userId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","username":{"value":"admin"}},"createdAt":"2023-11-14T09:30:00.000Z","checkpointedItems":[{"type":"checkpointedResource","rid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","resourceType":"DATASET","compassPath":{"value":"/My Project/My Dataset"},"orgMarkings":[]}],"justification":{"type":"acknowledgementJustification","prompt":"I acknowledge this action","title":"Export Confirmation"}}],"nextPageToken":"{\"token\":\"1771291126611\",\"recordRid\":\"ri.checkpoints.main.checkpoint.01932cec-a44d-41fc-8066-bfc15c1c4a4c\"}"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"rid":"ri.checkpoints.main.checkpoint.a1b2c3d4-e5f6-7890-abcd-ef1234567890","type":"CONTOUR_EXPORT","scope":"USER_SCOPED","actingUser":{"userId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","username":{"value":"admin"}},"createdAt":"2023-11-14T09:30:00.000Z","checkpointedItems":[{"type":"checkpointedResource","rid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","resourceType":"DATASET","compassPath":{"value":"/My Project/My Dataset"},"orgMarkings":[]}],"justification":{"type":"acknowledgementJustification","prompt":"I acknowledge this action","title":"Export Confirmation"}}],"nextPageToken":"{\"token\":\"1771291126611\",\"recordRid\":\"ri.checkpoints.main.checkpoint.01932cec-a44d-41fc-8066-bfc15c1c4a4c\"}"}

### Error Responses

| name | description |
| --- | --- |
| SearchRecordsPermissionDenied | Could not search the Record. |
