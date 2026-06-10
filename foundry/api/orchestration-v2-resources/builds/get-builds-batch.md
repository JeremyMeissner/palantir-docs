---
source_url: "https://www.palantir.com/docs/foundry/api/orchestration-v2-resources/builds/get-builds-batch/"
title: "Get Builds Batch \u2022 API Reference"
---
# Get Builds Batch

## Endpoint

Execute multiple get requests on Build.

Users are allowed to make a maximum of **4 requests per second** and **25 concurrent requests**.

The maximum batch size for this endpoint is 100.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:orchestration-read`.

**operationId:** v2.getBuildsBatch

**path:** /api/v2/orchestration/builds/getBatch

### Operation Type

### Scopes

| name |
| --- |
| api:orchestration-read |

### Request

#### Body

**name:** body

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| GetBuildsBatchRequestElement | objectType | True |  |

**example:** [{"buildRid":"ri.foundry.main.build.a4386b7e-d546-49be-8a36-eefc355f5c58"}]

### Response

#### Body

**name:** GetBuildsBatchResponse

**example:** {"data":{"ri.foundry.main.build.a4386b7e-d546-49be-8a36-eefc355f5c58":{"abortOnFailure":false,"createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","retryBackoffDuration":{"unit":"SECONDS","value":30},"retryCount":1,"fallbackBranches":[],"scheduleRid":"ri.scheduler.main.schedule.5ad5c340-59f3-4a60-9fc6-161bb984f871","branchName":"master","createdTime":"2003-05-06T12:34:56.789Z","jobRids":["ri.foundry.main.job.aaf94076-d773-4732-a1df-3b638eb50448"],"finishedTime":"2003-05-06T12:34:56.789Z","rid":"ri.foundry.main.build.a4386b7e-d546-49be-8a36-eefc355f5c58","status":"RUNNING"}}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | mapType | False |  |

**example:** {"data":{"ri.foundry.main.build.a4386b7e-d546-49be-8a36-eefc355f5c58":{"abortOnFailure":false,"createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","retryBackoffDuration":{"unit":"SECONDS","value":30},"retryCount":1,"fallbackBranches":[],"scheduleRid":"ri.scheduler.main.schedule.5ad5c340-59f3-4a60-9fc6-161bb984f871","branchName":"master","createdTime":"2003-05-06T12:34:56.789Z","jobRids":["ri.foundry.main.job.aaf94076-d773-4732-a1df-3b638eb50448"],"finishedTime":"2003-05-06T12:34:56.789Z","rid":"ri.foundry.main.build.a4386b7e-d546-49be-8a36-eefc355f5c58","status":"RUNNING"}}}
