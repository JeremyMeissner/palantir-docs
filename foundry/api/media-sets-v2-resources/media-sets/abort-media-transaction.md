---
source_url: "https://www.palantir.com/docs/foundry/api/media-sets-v2-resources/media-sets/abort-media-transaction/"
title: "Abort Media Transaction \u2022 API Reference"
---
# Abort Media Transaction

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Aborts an open transaction. Items uploaded to the media set during this transaction will be deleted.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:mediasets-write`.

**operationId:** v2.abortMediaTransaction

**path:** /api/v2/mediasets/{mediaSetRid}/transactions/{transactionId}/abort

### Operation Type

### Scopes

| name |
| --- |
| api:mediasets-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mediaSetRid | stringType | True | The Resource Identifier (RID) of a Media Set in Foundry. |
| transactionId | stringType | True | An identifier which represents a transaction on a media set. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |
