---
source_url: "https://www.palantir.com/docs/foundry/api/notepad-v2-resources/export-jobs/get-export-job/"
title: "Get Export Job \u2022 API Reference"
---
# Get Export Job

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Loads an ExportJob. This endpoint is used to monitor job progress.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:notepad-export`.

**operationId:** v2.getExportJob

**path:** /api/v2/notepad/exportJobs/{exportJobRid}

### Operation Type

### Scopes

| name |
| --- |
| api:notepad-export |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| exportJobRid | stringType | True | The unique identifier for an ExportJob |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** ExportJob

**example:** {"rid":"ri.notepad.main.export-job.ef32c039-353c-4555-9704-eacfdfaa2c1c","status":{"type":"running"}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The unique identifier for an ExportJob |
| status | unionType | True | The status of an export job |

**example:** {"rid":"ri.notepad.main.export-job.ef32c039-353c-4555-9704-eacfdfaa2c1c","status":{"type":"running"}}

### Error Responses

| name | description |
| --- | --- |
| ExportJobNotFound | The given ExportJob could not be found. |
