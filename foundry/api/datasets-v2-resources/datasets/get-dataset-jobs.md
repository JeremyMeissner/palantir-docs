---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/datasets/get-dataset-jobs/"
title: "Get Dataset Jobs \u2022 API Reference"
---
# Get Dataset Jobs

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Get the RIDs of the Jobs for the given dataset. By default, returned Jobs are sorted in descending order by the Job start time.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-read`.

**operationId:** v2.getDatasetJobs

**path:** /api/v2/datasets/{datasetRid}/jobs

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of a Dataset. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branchName | stringType | False | The name of the Branch. If none is provided, the default Branch name - `master` for most enrollments - will be used. |
| pageSize | integerType | False | Max number of results to return. A limit of 1000 on if no limit is supplied in the search request |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** GetDatasetJobsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| where | unionType | False | Query for getting jobs on given dataset. |
| orderBy | listType | False |  |

**example:** {"orderBy":[{"sortType":"BY_STARTED_TIME","sortDirection":"DESCENDING"}],"where":{"type":"timeFilter","field":"SUBMITTED_TIME","comparisonType":"GTE","value":"2020-09-30T14:30:00Z"}}

### Response

#### Body

**name:** GetJobResponse

**example:** {"data":[{"jobRid":"ri.foundry.main.job.aaf94076-d773-4732-a1df-3b638eb50448"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"jobRid":"ri.foundry.main.job.aaf94076-d773-4732-a1df-3b638eb50448"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| BranchNotFound | The requested branch could not be found, or the client token does not have access to it. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
| GetDatasetJobsPermissionDenied | Could not jobs the Dataset. |
