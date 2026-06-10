---
source_url: "https://www.palantir.com/docs/foundry/api/audit-v2-resources/log-files/list-log-files/"
title: "List Log Files \u2022 API Reference"
---
# List Log Files

## Endpoint

Lists all LogFiles.

This is a paged endpoint. Each page may be smaller or larger than the requested page size. However, it is guaranteed that if there are more results available, the `nextPageToken` field will be populated. To get the next page, make the same request again, but set the value of the `pageToken` query parameter to be value of the `nextPageToken` value of the previous response. If there is no `nextPageToken` field in the response, you are on the last page.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:audit-read`.

**operationId:** v2.listLogFiles

**path:** /api/v2/audit/organizations/{organizationRid}/logFiles

### Operation Type

### Scopes

| name |
| --- |
| api:audit-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| organizationRid | stringType | True |  |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| startDate | stringType | False | List log files for audit events starting from this date. This parameter is required for the initial request (when `pageToken` is not provided). |
| endDate | stringType | False | List log files for audit events up until this date (inclusive). If absent, defaults to no end date. Use the returned `nextPageToken` to continually poll the  `listLogFiles` endpoint to list the latest available logs. |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

### Response

#### Body

**name:** ListLogFilesResponse

**example:** {"data":[{"id":"S2VlcEV4cGxvcmluZw=="}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"id":"S2VlcEV4cGxvcmluZw=="}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| ListLogFilesPermissionDenied | The provided token does not have permission to list audit log files. |
| MissingStartDate | Start date is required to list audit log files. |
