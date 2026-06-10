---
source_url: "https://www.palantir.com/docs/foundry/api/media-sets-v2-resources/media-sets/register-media-item/"
title: "Register Media Item \u2022 API Reference"
---
# Register Media Item

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Registers a media item that currently resides in a federated media store. Registration will validate the item
against the media set's schema and perform initial metadata extraction.
This endpoint is only applicable for federated media sets.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:mediasets-write`.

**operationId:** v2.registerMediaItem

**path:** /api/v2/mediasets/{mediaSetRid}/items/register

### Operation Type

### Scopes

| name |
| --- |
| api:mediasets-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mediaSetRid | stringType | True | The Resource Identifier (RID) of a Media Set in Foundry. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branchName | stringType | False | Specifies the specific branch by name to which this media item will be registered. |
| viewRid | stringType | False | Specifies the specific view by rid to which this media item will be registered. |
| transactionId | stringType | False | The id of the transaction associated with this request. Required for transactional media sets. |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |

### Request

#### Body

Request to register a media item from a federated store.

**name:** RegisterMediaItemRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| physicalItemName | stringType | True | The relative path within the federated media store where the media item exists. |
| mediaItemPath | stringType | False | A user-specified identifier for a media item within a media set. Paths must be less than 256 characters long. If multiple items are written to the same media set at the same path, then when retrieving by path the media item which was written last is returned. |

### Response

#### Body

Response after successfully registering a media item.

**name:** RegisterMediaItemResponse

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| mediaItemRid | stringType | True | The Resource Identifier (RID) of an individual Media Item within a Media Set in Foundry. |
| mediaType | stringType | True | The [media type](https://www.iana.org/assignments/media-types/media-types.xhtml) of the file or attachment. Examples: `application/json`, `application/pdf`, `application/octet-stream`, `image/jpeg` |
