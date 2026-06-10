---
source_url: "https://www.palantir.com/docs/foundry/api/media-sets-v2-resources/media-sets/get-media-item-rid-by-path/"
title: "Get Media Item Rid By Path \u2022 API Reference"
---
# Get Media Item Rid By Path

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Returns the media item RID for the media item with the specified path.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:mediasets-read`.

**operationId:** v2.getMediaItemRidByPath

**path:** /api/v2/mediasets/{mediaSetRid}/items/getRidByPath

### Operation Type

### Scopes

| name |
| --- |
| api:mediasets-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mediaSetRid | stringType | True | The RID of the media set. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mediaItemPath | stringType | True | The path of the media item. |
| branchName | stringType | False | Specifies the specific branch by name in which to search for this media item. May not be provided if branch rid or view rid are provided. |
| branchRid | stringType | False | Specifies the specific branch by rid in which to search for this media item. May not be provided if branch name or view rid are provided. |
| viewRid | stringType | False | Specifies the specific view by rid in which to search for this media item. May not be provided if branch name or branch rid are provided. |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |

### Response

#### Body

**name:** GetMediaItemRidByPathResponse

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| mediaItemRid | stringType | False | The Resource Identifier (RID) of an individual Media Item within a Media Set in Foundry. |
