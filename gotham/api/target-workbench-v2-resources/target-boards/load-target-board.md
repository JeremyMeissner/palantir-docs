---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench-v2-resources/target-boards/load-target-board/"
title: "Load Target Board \u2022 API Reference"
---
# Load Target Board

## Endpoint

Load Target Board by RID.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:target-read`.

**operationId:** v2.loadTargetBoard

**path:** /api/v2/targetWorkbench/targetBoards/{targetBoardRid}/load

### Operation Type

### Scopes

| name |
| --- |
| api:target-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| targetBoardRid | stringType | True | The unique identifier for a Target Board |

### Response

#### Body

Success response with the requested Target Board.

**name:** LoadTargetBoardResponse

**example:** {"targetBoard":{"targetColumnIds":{"bi.2a46fbf6-ff93-4710-951a-015ed5c92441*ri.gotham-artifact.0-0.target.1":{"columnId":"EXECUTION"},"bi.8a66fbf3-ff93-4710-951a-015ee5c92441*ri.gotham-artifact.0-0.target.2":{"columnId":"EXECUTION"}},"highPriorityTargetList":"ri.gotham-artifact.0-0.hptl.example","configuration":{"columns":[{"id":"EXECUTION","name":"IN PROGRESS","color":"RED"}],"targetIdentifiers":["CUSTOM"]},"name":"Example target board name.","description":"Example target board description.","rid":"ri.gotham-artifact.0-0.target-board.example","targets":["bi.2a46fbf6-ff93-4710-951a-015ed5c92441*ri.gotham-artifact.0-0.target.1","bi.8a66fbf3-ff93-4710-951a-015ee5c92441*ri.gotham-artifact.0-0.target.2"]},"baseRevisionId":1}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| targetBoard | objectType | True |  |
| baseRevisionId | stringType | True | The current version of the Target Board to be modified. The archive operation will be transformed against any concurrent operations made since this version. If there are any conflicting edits that result in changes to these operations when they're applied, that will be noted in the response. |

**example:** {"targetBoard":{"targetColumnIds":{"bi.2a46fbf6-ff93-4710-951a-015ed5c92441*ri.gotham-artifact.0-0.target.1":{"columnId":"EXECUTION"},"bi.8a66fbf3-ff93-4710-951a-015ee5c92441*ri.gotham-artifact.0-0.target.2":{"columnId":"EXECUTION"}},"highPriorityTargetList":"ri.gotham-artifact.0-0.hptl.example","configuration":{"columns":[{"id":"EXECUTION","name":"IN PROGRESS","color":"RED"}],"targetIdentifiers":["CUSTOM"]},"name":"Example target board name.","description":"Example target board description.","rid":"ri.gotham-artifact.0-0.target-board.example","targets":["bi.2a46fbf6-ff93-4710-951a-015ed5c92441*ri.gotham-artifact.0-0.target.1","bi.8a66fbf3-ff93-4710-951a-015ee5c92441*ri.gotham-artifact.0-0.target.2"]},"baseRevisionId":1}

### Error Responses

| name | description |
| --- | --- |
| TargetBoardNotFound | Cannot find target board from provided rid. |
| LoadTargetBoardPermissionDenied | Could not load the TargetBoard. |
