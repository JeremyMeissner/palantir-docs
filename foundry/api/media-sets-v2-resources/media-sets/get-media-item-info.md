---
source_url: "https://www.palantir.com/docs/foundry/api/media-sets-v2-resources/media-sets/get-media-item-info/"
title: "Get Media Item Info \u2022 API Reference"
---
# Get Media Item Info

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Gets information about the media item.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:mediasets-read`.

**operationId:** v2.getMediaItemInfo

**path:** /api/v2/mediasets/{mediaSetRid}/items/{mediaItemRid}

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

**name:** GetMediaItemInfoResponse

**example:** {"viewRid":"ri.mio.main.view.1","logicalTimestamp":12345,"path":"example.png","attribution":{"creatorId":1,"creationTimestamp":"2020-07-10 15:00:00.000"},"originallyUploadedFileMimeType":"image/png"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| viewRid | stringType | True | The Resource Identifier (RID) of a single View of a Media Set. A Media Set View is an independent collection of Media Items. |
| path | stringType | False | A user-specified identifier for a media item within a media set. Paths must be less than 256 characters long. If multiple items are written to the same media set at the same path, then when retrieving by path the media item which was written last is returned. |
| logicalTimestamp | stringType | True | A number representing a logical ordering to be used for transactions, etc. This can be interpreted as a timestamp in microseconds, but may differ slightly from system clock time due  to clock drift and slight adjustments for the sake of ordering.  Only positive timestamps (representing times after epoch) are supported. |
| attribution | objectType | False |  |
| originallyUploadedFileMimeType | stringType | False | The [media type](https://www.iana.org/assignments/media-types/media-types.xhtml) of the file or attachment. Examples: `application/json`, `application/pdf`, `application/octet-stream`, `image/jpeg` |
| mimeType | stringType | False | The [media type](https://www.iana.org/assignments/media-types/media-types.xhtml) of the file or attachment. Examples: `application/json`, `application/pdf`, `application/octet-stream`, `image/jpeg` |
| sizeBytes | integerType | False | The size of the media item in bytes. |

**example:** {"viewRid":"ri.mio.main.view.1","logicalTimestamp":12345,"path":"example.png","attribution":{"creatorId":1,"creationTimestamp":"2020-07-10 15:00:00.000"},"originallyUploadedFileMimeType":"image/png"}
