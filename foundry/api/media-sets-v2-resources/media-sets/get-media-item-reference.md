---
source_url: "https://www.palantir.com/docs/foundry/api/media-sets-v2-resources/media-sets/get-media-item-reference/"
title: "Get Media Item Reference \u2022 API Reference"
---
# Get Media Item Reference

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Gets the [media reference](/docs/foundry/data-integration/media-sets/#media-references) for this media item.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:mediasets-read`.

**operationId:** v2.getMediaItemReference

**path:** /api/v2/mediasets/{mediaSetRid}/items/{mediaItemRid}/reference

### Operation Type

### Scopes

| name |
| --- |
| api:mediasets-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mediaSetRid | stringType | True | The RID of the media set. |
| mediaItemRid | stringType | True | The RID of the media item. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |

### Response

#### Body

The representation of a media reference.

**name:** MediaReference

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| mimeType | stringType | True | The [media type](https://www.iana.org/assignments/media-types/media-types.xhtml) of the file or attachment. Examples: `application/json`, `application/pdf`, `application/octet-stream`, `image/jpeg` |
| reference | unionType | True | A union of the types supported by media reference properties. |
