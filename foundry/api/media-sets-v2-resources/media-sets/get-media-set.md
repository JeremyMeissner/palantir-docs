---
source_url: "https://www.palantir.com/docs/foundry/api/media-sets-v2-resources/media-sets/get-media-set/"
title: "Get Media Set \u2022 API Reference"
---
# Get Media Set

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Gets information about the media set.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:mediasets-read`.

**operationId:** v2.getMediaSet

**path:** /api/v2/mediasets/{mediaSetRid}

### Operation Type

### Scopes

| name |
| --- |
| api:mediasets-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mediaSetRid | stringType | True | The Resource Identifier (RID) of a Media Set in Foundry. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |

### Response

#### Body

Information about a media set.

**name:** GetMediaSetResponse

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The Resource Identifier (RID) of a Media Set in Foundry. |
| mediaSchema | enumType | True | The schema type of a media set, indicating what type of media items it can contain. |
| defaultBranchName | stringType | True | A name for a media set branch. Valid branch names must be (a) non-empty, (b) less than 256 characters, and  (c) not a valid ResourceIdentifier. |
| transactionPolicy | unionType | True | The transaction policy for a media set, determining how writes are handled. |
| pathsRequired | booleanType | True | Whether media items in this media set require paths. |
