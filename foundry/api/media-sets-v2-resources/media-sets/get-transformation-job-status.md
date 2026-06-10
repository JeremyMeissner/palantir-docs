---
source_url: "https://www.palantir.com/docs/foundry/api/media-sets-v2-resources/media-sets/get-transformation-job-status/"
title: "Get Transformation Job Status \u2022 API Reference"
---
# Get Transformation Job Status

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Gets the status of a transformation job.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:mediasets-transform`.

**operationId:** v2.getTransformationJobStatus

**path:** /api/v2/mediasets/{mediaSetRid}/items/{mediaItemRid}/transformationJobs/{transformationJobId}

### Operation Type

### Scopes

| name |
| --- |
| api:mediasets-transform |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mediaSetRid | stringType | True | The RID of the media set. |
| mediaItemRid | stringType | True | The RID of the media item. |
| transformationJobId | stringType | True | The ID of the transformation job. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |

### Response

#### Body

The status of the transformation job.

**name:** GetTransformationJobStatusResponse

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| status | enumType | True | The status of a transformation job. |
| jobId | stringType | True | An identifier for a media item transformation job. |
