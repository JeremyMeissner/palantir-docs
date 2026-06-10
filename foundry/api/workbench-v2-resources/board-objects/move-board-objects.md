---
source_url: "https://www.palantir.com/docs/foundry/api/workbench-v2-resources/board-objects/move-board-objects/"
title: "Move Board Objects \u2022 API Reference"
---
# Move Board Objects

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Moves Foundry Objects from their current state to a different state on a Workbench Board.
This operation preserves the objects' board item identifiers and edit history, allowing users
to track the objects' progression through workflow states.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:workbench-write`.

**operationId:** v2.moveBoardObjects

**path:** /api/v2/workbench/boards/{boardRid}/objects/move

### Operation Type

### Scopes

| name |
| --- |
| api:workbench-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| boardRid | stringType | True | The unique identifier for a Workbench Board |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** MoveBoardObjectsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| objectRids | listType | False | The RIDs of the Foundry Objects to move |
| stateId | stringType | True | The destination state (column) to move the objects to |

**example:** {"objectRids":["ri.phonograph2-objects.main.object.48668bf6-8878-48d2-b8f8-f0017593feb5"],"stateId":"3fa85f64-5717-4562-b3fc-2c963f66afa6"}

### Response

#### Body

An empty response object indicating the request was successful

**name:** EmptySuccessResponse

### Error Responses

| name | description |
| --- | --- |
| ObjectNotOnBoard | One or more objects are not on the specified board and cannot be moved. |
| BoardStateNotFound | The specified state does not exist on the board. |
| BoardOperationNotSupported | The requested operation cannot be performed on this board. |
| MoveBoardObjectsPermissionDenied | Could not move the BoardObject. |
