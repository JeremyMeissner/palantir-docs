---
source_url: "https://www.palantir.com/docs/foundry/api/media-sets-v2-resources/media-sets/get-media-item-metadata/"
title: "Get Media Item Metadata \u2022 API Reference"
---
# Get Media Item Metadata

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Gets detailed metadata about the media item, including type-specific information
such as dimensions for images, duration for audio/video, page count for documents, etc.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:mediasets-read`.

**operationId:** v2.getMediaItemMetadata

**path:** /api/v2/mediasets/{mediaSetRid}/items/{mediaItemRid}/metadata

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

Detailed metadata about a media item, including type-specific information such as dimensions for images,
duration for audio/video, page count for documents, etc.

**name:** MediaItemMetadata

**example:** {"type":"imagery","format":"PNG","dimensions":{"width":1920,"height":1080},"sizeBytes":2048576}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| document | objectType | False | Metadata for document media items. |
| imagery | objectType | False | Metadata for imagery (image) media items. |
| spreadsheet | objectType | False | Metadata for spreadsheet media items. |
| untyped | objectType | False | Metadata for untyped media items (media items without a recognized type). |
| audio | objectType | False | Metadata for audio media items. |
| model3d | objectType | False | Metadata for 3D model media items. |
| video | objectType | False | Metadata for video media items. |
| dicom | objectType | False | Metadata for DICOM (Digital Imaging and Communications in Medicine) media items. |
| email | objectType | False | Metadata for email media items. |

**example:** {"type":"imagery","format":"PNG","dimensions":{"width":1920,"height":1080},"sizeBytes":2048576}
