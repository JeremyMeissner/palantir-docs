---
source_url: "https://www.palantir.com/docs/foundry/api/notepad-v2-resources/generation-jobs/get-generation-job/"
title: "Get Generation Job \u2022 API Reference"
---
# Get Generation Job

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Load an existing GenerationJob. This is used to monitor job progress.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:notepad-write`.

**operationId:** v2.getGenerationJob

**path:** /api/v2/notepad/templates/{templateRid}/generationJobs/{generationJobRid}

### Operation Type

### Scopes

| name |
| --- |
| api:notepad-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| templateRid | stringType | True | The unique identifier for a Template |
| generationJobRid | stringType | True | The unique identifier for a GenerationJob |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** GenerationJob

**example:** {"rid":"ri.notepad.main.generation-job.ab12c039-353c-4555-9704-eacfdfaa2c1c","status":{"type":"running"}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The unique identifier for a GenerationJob |
| status | unionType | True | The status of a GenerationJob |

**example:** {"rid":"ri.notepad.main.generation-job.ab12c039-353c-4555-9704-eacfdfaa2c1c","status":{"type":"running"}}

### Error Responses

| name | description |
| --- | --- |
| GenerationJobNotFound | The given GenerationJob could not be found. |
