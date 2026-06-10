---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench-v2-resources/target-boards/delete-target-board/"
title: "Delete Target Board \u2022 API Reference"
---
# Delete Target Board

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Archive a Target Board by RID.
The user is required to have OWN permissions on the target.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:target-write`.

**operationId:** v2.deleteTargetBoard

**path:** /api/v2/targetWorkbench/targetBoards/{targetBoardRid}

### Operation Type

### Scopes

| name |
| --- |
| api:target-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| targetBoardRid | stringType | True | The unique identifier for a Target Board |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Error Responses

| name | description |
| --- | --- |
| UserHasNoOwnerPerms | The user is required to have owner permissions on the artifact. |
| DeleteTargetBoardPermissionDenied | Could not delete the TargetBoard. |
