---
source_url: "https://www.palantir.com/docs/gotham/api/revdb-resources/media/get-media-content/"
title: "Get media content \u2022 API Reference"
---
# Get media content

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Get the content of media.

**operationId:** v1.getMediaContent

**path:** /api/gotham/v1/media/{mediaRid}/content

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mediaRid | stringType | True | The RID of the media. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Response

#### Body

Success response.

**name:** body

##### Format
