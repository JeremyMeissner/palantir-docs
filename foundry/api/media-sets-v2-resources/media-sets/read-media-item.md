---
source_url: "https://www.palantir.com/docs/foundry/api/media-sets-v2-resources/media-sets/read-media-item/"
title: "Read Media Item \u2022 API Reference"
---
# Read Media Item

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Gets the content of a media item.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:mediasets-read`.

**operationId:** v2.readMediaItem

**path:** /api/v2/mediasets/{mediaSetRid}/items/{mediaItemRid}/content

### Operation Type

### Scopes

| name |
| --- |
| api:mediasets-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mediaSetRid | stringType | True | The Resource Identifier (RID) of a Media Set in Foundry. |
| mediaItemRid | stringType | True | The Resource Identifier (RID) of an individual Media Item within a Media Set in Foundry. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |

### Response

#### Body

The content stream.

**name:** body

##### Format
