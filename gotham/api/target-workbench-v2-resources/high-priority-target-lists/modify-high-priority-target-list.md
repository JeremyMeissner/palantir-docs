---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench-v2-resources/high-priority-target-lists/modify-high-priority-target-list/"
title: "Modify High Priority Target List \u2022 API Reference"
---
# Modify High Priority Target List

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Modify a High Priority Target (HPTL) List by RID.

Sets the current state of a HPTL. Any fields not supplied, except target board, will result in removal if there was a value present. 
Trying to set target board to empty when there is already a value will result in an INVALID_ARGUMENT exception. 
You cannot modify the target board field if a value is already set.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:target-write`.

**operationId:** v2.modifyHighPriorityTargetList

**path:** /api/v2/targetWorkbench/highPriorityTargetLists/{highPriorityTargetListRid}/modify

### Operation Type

### Scopes

| name |
| --- |
| api:target-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| highPriorityTargetListRid | stringType | True | The unique identifier for a High Priority Target List |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** ModifyHighPriorityTargetListRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| targetBoard | stringType | False | The unique identifier for a Target Board |
| targets | listType | False | A list of HighPriorityTargetListTargets |
| areaObjectRid | stringType | False | The primary key/unique identifier of an object, useful for interacting with Gotham APIs to load and mutate objects. |
| areaGeo | objectType | False | A Polygon representing the area where this High Priority Target List is applicable. If areaObjectRid exists, that field/area will be used and this field will be ignored. |
| targetAois | listType | False |  |
| baseRevisionId | integerType | True | The current version of the retrieved HighPriorityTargetList. Any modifying operations should be accompanied by this version to avoid concurrent operations made since this version. If there are any conflicting edits that result in changes to these operations when they are applied, it will be noted in the response. |

**example:** {"targetBoard":"ri.gotham-artifact.0-0.target-board.example","areaGeo":{"points":[{"elevation":0.0,"latitude":0.0,"longitude":0.0}]},"areaObjectRid":"ri.gotham.123-456.object-internal.example","baseRevisionId":1,"targets":[{"targetSubtypes":["Red Car"],"when":"ACQUIRED"}]}

### Response

#### Body

An empty response object indicating the request was successful.

**name:** EmptySuccessResponse

### Error Responses

| name | description |
| --- | --- |
| HighPriorityTargetListNotFound | Cannot find High Priority Target List from provided RID |
| ModifyHighPriorityTargetListPermissionDenied | Could not modify the HighPriorityTargetList. |
