---
source_url: "https://www.palantir.com/docs/foundry/api/workbench-v2-resources/board-objects/add-board-objects/"
title: "Add Board Objects \u2022 API Reference"
---
# Add Board Objects

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Adds Foundry Objects to a Workbench Board. This operation links the objects to the board,
allowing them to be tracked within the board's workflow. If no state is specified, the objects
will be placed in the board's default state (first column).

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:workbench-write`.

**operationId:** v2.addBoardObjects

**path:** /api/v2/workbench/boards/{boardRid}/objects/add

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

**name:** AddBoardObjectsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| objectRids | listType | False | The RIDs of the Foundry Objects to add to the board |
| stateId | stringType | False | Optional state (column) to place the objects in. If not specified, the objects will be placed in the board's default state (the first state in the board's configured order). |

**example:** {"objectRids":["ri.phonograph2-objects.main.object.48668bf6-8878-48d2-b8f8-f0017593feb5"],"stateId":"3fa85f64-5717-4562-b3fc-2c963f66afa6"}

### Response

#### Body

An empty response object indicating the request was successful

**name:** EmptySuccessResponse

### Error Responses

| name | description |
| --- | --- |
| ObjectAlreadyOnBoard | One or more objects are already on the specified board and cannot be added again. |
| BoardStateNotFound | The specified state does not exist on the board. |
| BoardHasNoDefaultState | The board has no default state configured and no state was specified in the request. |
| ObjectNotFound | One or more Foundry Objects could not be found or accessed. |
| ObjectTypeNotSupported | One or more objects do not implement the interface type or object type required by the board. |
| BoardInterfaceTypeNotSet | The board requires an interface type to be configured before objects can be added. |
| ObjectSecurityNotSatisfied | One or more objects do not satisfy the security requirements of the board. |
| BoardExceededItemLimit | Adding the requested objects would exceed the maximum number of items allowed on the board. |
| BoardOperationNotSupported | The requested operation cannot be performed on this board. |
| AddBoardObjectsPermissionDenied | Could not add the BoardObject. |
