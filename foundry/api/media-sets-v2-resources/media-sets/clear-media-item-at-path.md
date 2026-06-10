---
source_url: "https://www.palantir.com/docs/foundry/api/media-sets-v2-resources/media-sets/clear-media-item-at-path/"
title: "Clear Media Item At Path \u2022 API Reference"
---
# Clear Media Item At Path

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Clears (soft-deletes) the media item at the specified path within a media set, making it and all older
media items at that path un-retrievable.

A branch name, branch RID, or view RID may optionally be specified. If none is specified,
the item will be cleared from the default branch. If more than one is specified, an error is thrown.

For transactional media sets, a transaction ID must be provided. The deletion will not be
visible until the transaction is committed.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:mediasets-write`.

**operationId:** v2.clearMediaItemAtPath

**path:** /api/v2/mediasets/{mediaSetRid}/items/clearAtPath

### Operation Type

### Scopes

| name |
| --- |
| api:mediasets-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mediaSetRid | stringType | True | The RID of the media set. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mediaItemPath | stringType | True | The path of the media item to clear. |
| branchName | stringType | False | Specifies the specific branch by name from which this media item will be cleared. May not be provided if branch rid or view rid are provided. |
| branchRid | stringType | False | Specifies the specific branch by rid from which this media item will be cleared. May not be provided if branch name or view rid are provided. |
| viewRid | stringType | False | Specifies the specific view by rid from which this media item will be cleared. May not be provided if branch name or branch rid are provided. |
| transactionId | stringType | False | The ID of the transaction associated with this request. Required if this is a transactional media set. |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |
