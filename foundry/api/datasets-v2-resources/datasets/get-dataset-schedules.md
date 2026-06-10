---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/datasets/get-dataset-schedules/"
title: "Get Dataset Schedules \u2022 API Reference"
---
# Get Dataset Schedules

## Endpoint

Get the RIDs of the Schedules that target the given Dataset.

Note: It may take up to an hour for recent changes to schedules to be reflected in this response,
especially for schedules managed by Marketplace. This operation will return outdated results in the
meantime.

Third-party applications using this endpoint via OAuth2 must request the following operation scopes: `api:orchestration-read api:datasets-read`.

**operationId:** v2.getDatasetSchedules

**path:** /api/v2/datasets/{datasetRid}/getSchedules

### Operation Type

### Scopes

| name |
| --- |
| api:orchestration-read |
| api:datasets-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of a Dataset. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branchName | stringType | False | The name of the Branch. If none is provided, the default Branch name - `master` for most enrollments - will be used. |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

### Response

#### Body

**name:** ListSchedulesResponse

**example:** {"data":["ri.scheduler.main.schedule.5ad5c340-59f3-4a60-9fc6-161bb984f871"],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":["ri.scheduler.main.schedule.5ad5c340-59f3-4a60-9fc6-161bb984f871"],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| BranchNotFound | The requested branch could not be found, or the client token does not have access to it. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
| GetDatasetSchedulesPermissionDenied | Could not getSchedules the Dataset. |
