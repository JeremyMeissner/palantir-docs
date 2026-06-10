---
source_url: "https://www.palantir.com/docs/foundry/api/media-sets-v2-resources/media-sets/transform-media-item/"
title: "Transform Media Item \u2022 API Reference"
---
# Transform Media Item

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Initiates a transformation on a media item. Returns a job ID that can be used to check the status and retrieve 
the result of the transformation.

Transforming a media item requires that you are able to read the media item, either via `api:mediasets-read` or
via a `MediaItemReadToken`

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:mediasets-transform`.

**operationId:** v2.transformMediaItem

**path:** /api/v2/mediasets/{mediaSetRid}/items/{mediaItemRid}/transform

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

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |

### Request

#### Body

Request to transform a media item.

**name:** TransformMediaItemRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| transformation | unionType | True | A transformation to apply to a media item. Each variant specifies the type of transformation and any parameters required for the operation. |

**example:** {"transformation":{"type":"image","encoding":{"type":"webp"},"operations":[{"type":"resize","width":800,"height":600}]}}

### Response

#### Body

The transformation was initiated successfully.

**name:** TransformMediaItemResponse

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| status | enumType | True | The status of a transformation job. |
| jobId | stringType | True | An identifier for a media item transformation job. |
