---
source_url: "https://www.palantir.com/docs/foundry/api/orchestration-v2-resources/builds/list-jobs-of-build/"
title: "List Jobs Of Build \u2022 API Reference"
---
# List Jobs Of Build

## Endpoint

Get the Jobs in the Build.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:orchestration-read`.

**operationId:** v2.listJobsOfBuild

**path:** /api/v2/orchestration/builds/{buildRid}/jobs

### Operation Type

### Scopes

| name |
| --- |
| api:orchestration-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| buildRid | stringType | True | The RID of a Build. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

### Response

#### Body

**name:** ListJobsOfBuildResponse

**example:** {"data":[{"startedTime":"2003-05-06T12:34:56.789Z","jobStatus":"WAITING","buildRid":"ri.foundry.main.build.a4386b7e-d546-49be-8a36-eefc355f5c58","finishedTime":"2003-05-06T12:34:56.789Z","rid":"ri.foundry.main.job.aaf94076-d773-4732-a1df-3b638eb50448","latestAttemptStartTime":"2003-05-06T12:34:56.789Z"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"startedTime":"2003-05-06T12:34:56.789Z","jobStatus":"WAITING","buildRid":"ri.foundry.main.build.a4386b7e-d546-49be-8a36-eefc355f5c58","finishedTime":"2003-05-06T12:34:56.789Z","rid":"ri.foundry.main.job.aaf94076-d773-4732-a1df-3b638eb50448","latestAttemptStartTime":"2003-05-06T12:34:56.789Z"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}
