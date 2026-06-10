---
source_url: "https://www.palantir.com/docs/foundry/api/orchestration-v2-resources/jobs/get-jobs-batch/"
title: "Get Jobs Batch \u2022 API Reference"
---
# Get Jobs Batch

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Execute multiple get requests on Job.

Users are allowed to make a maximum of **4 requests per second** and **25 concurrent requests**.

The maximum batch size for this endpoint is 500.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:orchestration-read`.

**operationId:** v2.getJobsBatch

**path:** /api/v2/orchestration/jobs/getBatch

### Operation Type

### Scopes

| name |
| --- |
| api:orchestration-read |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** body

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| GetJobsBatchRequestElement | objectType | True |  |

**example:** [{"jobRid":"ri.foundry.main.job.aaf94076-d773-4732-a1df-3b638eb50448"}]

### Response

#### Body

**name:** GetJobsBatchResponse

**example:** {"data":{"ri.foundry.main.job.aaf94076-d773-4732-a1df-3b638eb50448":{"startedTime":"2003-05-06T12:34:56.789Z","jobStatus":"WAITING","buildRid":"ri.foundry.main.build.a4386b7e-d546-49be-8a36-eefc355f5c58","finishedTime":"2003-05-06T12:34:56.789Z","rid":"ri.foundry.main.job.aaf94076-d773-4732-a1df-3b638eb50448","latestAttemptStartTime":"2003-05-06T12:34:56.789Z"}}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | mapType | False |  |

**example:** {"data":{"ri.foundry.main.job.aaf94076-d773-4732-a1df-3b638eb50448":{"startedTime":"2003-05-06T12:34:56.789Z","jobStatus":"WAITING","buildRid":"ri.foundry.main.build.a4386b7e-d546-49be-8a36-eefc355f5c58","finishedTime":"2003-05-06T12:34:56.789Z","rid":"ri.foundry.main.job.aaf94076-d773-4732-a1df-3b638eb50448","latestAttemptStartTime":"2003-05-06T12:34:56.789Z"}}}
