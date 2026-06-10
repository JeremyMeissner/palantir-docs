---
source_url: "https://www.palantir.com/docs/foundry/api/media-sets-v2-resources/media-sets/create-media-transaction/"
title: "Create Media Transaction \u2022 API Reference"
---
# Create Media Transaction

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Creates a new transaction. Items uploaded to the media set while this transaction is open will not be reflected until the transaction is committed.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:mediasets-write`.

**operationId:** v2.createMediaTransaction

**path:** /api/v2/mediasets/{mediaSetRid}/transactions

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
| branchName | stringType | False | The branch on which to open the transaction. Defaults to `master` for most enrollments. |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |

### Response

#### Body

An identifier which represents a transaction on a media set.

**name:** TransactionId

##### Format

**example:** {"transactionId":"550e8400-e29b-41d4-a716-446655440000"}

**example:** {"transactionId":"550e8400-e29b-41d4-a716-446655440000"}
