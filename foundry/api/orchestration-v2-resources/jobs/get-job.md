---
source_url: "https://www.palantir.com/docs/foundry/api/orchestration-v2-resources/jobs/get-job/"
title: "Get Job \u2022 API Reference"
---
# Get Job

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Get the Job with the specified rid.

Users are allowed to make a maximum of **4 requests per second** and **25 concurrent requests**.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:orchestration-read`.

**operationId:** v2.getJob

**path:** /api/v2/orchestration/jobs/{jobRid}

### Operation Type

### Scopes

| name |
| --- |
| api:orchestration-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| jobRid | stringType | True | The RID of a Job. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** Job

**example:** {"startedTime":"2003-05-06T12:34:56.789Z","jobStatus":"WAITING","buildRid":"ri.foundry.main.build.a4386b7e-d546-49be-8a36-eefc355f5c58","finishedTime":"2003-05-06T12:34:56.789Z","rid":"ri.foundry.main.job.aaf94076-d773-4732-a1df-3b638eb50448","latestAttemptStartTime":"2003-05-06T12:34:56.789Z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The RID of a Job. |
| buildRid | stringType | True | The RID of the Build that the Job belongs to. |
| startedTime | stringType | True | The time this job started waiting for the dependencies to be resolved. |
| latestAttemptStartTime | stringType | False | The time this job's latest attempt started running. This field may be empty or outdated if the job failed to start. |
| finishedTime | stringType | False | The time this job was finished. |
| jobStatus | enumType | True | The status of the job. |
| outputs | listType | False | Outputs of the Job. Only outputs with supported types are listed here; unsupported types are omitted. Currently supported types are Dataset and Media Set outputs. |

**example:** {"startedTime":"2003-05-06T12:34:56.789Z","jobStatus":"WAITING","buildRid":"ri.foundry.main.build.a4386b7e-d546-49be-8a36-eefc355f5c58","finishedTime":"2003-05-06T12:34:56.789Z","rid":"ri.foundry.main.job.aaf94076-d773-4732-a1df-3b638eb50448","latestAttemptStartTime":"2003-05-06T12:34:56.789Z"}

### Error Responses

| name | description |
| --- | --- |
| JobNotFound | The given Job could not be found. |
