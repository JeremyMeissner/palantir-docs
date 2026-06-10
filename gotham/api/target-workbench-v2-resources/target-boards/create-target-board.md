---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench-v2-resources/target-boards/create-target-board/"
title: "Create Target Board \u2022 API Reference"
---
# Create Target Board

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

By default, create a TargetBoard with default columns: IDENTIFIED TARGET, PRIORITIZED TARGET, IN COORDINATION, IN EXECUTION, COMPLETE.
Returns the RID of the created TargetBoard.
The `security.spaceRid` field defaults to your user's space if there is only one. Use the List Spaces endpoint at `/api/v2/filesystem/spaces` to get the spaces your user has access to.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:target-write`.

**operationId:** v2.createTargetBoard

**path:** /api/v2/targetWorkbench/targetBoards

### Operation Type

### Scopes

| name |
| --- |
| api:target-write |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** CreateTargetBoardRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| security | objectType | True | Security settings for the board |
| highPriorityTargetList | stringType | False |  |
| configuration | objectType | False | Configuration for a target board |
| name | stringType | True |  |
| description | stringType | False |  |

**example:** {"security":{"portionMarkings":["SENSITIVE"],"spaceRid":"ri.compass.main.folder.12345"},"highPriorityTargetList":"ri.gotham-artifact.0-0.hptl.example","configuration":{"columns":[{"id":"EXECUTION","name":"IN PROGRESS","color":"RED"}],"targetIdentifiers":["CUSTOM"]},"name":"Example target board name.","description":"Example target board description."}

### Response

#### Body

The created TargetBoard

**name:** TargetBoard

**example:** {"security":{"portionMarkings":["SENSITIVE"],"spaceRid":"ri.compass.main.folder.12345"},"highPriorityTargetList":"ri.gotham-artifact.0-0.hptl.example","configuration":{"columns":[{"id":"EXECUTION","name":"IN PROGRESS","color":"RED"}],"targetIdentifiers":["CUSTOM"]},"name":"Example target board name.","description":"Example target board description.","rid":"ri.gotham-artifact.0-0.target-board.example"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The unique identifier for a Target Board |
| name | stringType | True |  |
| description | stringType | False |  |
| highPriorityTargetList | stringType | False |  |
| configuration | objectType | False | Configuration for a target board |
| security | objectType | True | Security settings for the board |

**example:** {"security":{"portionMarkings":["SENSITIVE"],"spaceRid":"ri.compass.main.folder.12345"},"highPriorityTargetList":"ri.gotham-artifact.0-0.hptl.example","configuration":{"columns":[{"id":"EXECUTION","name":"IN PROGRESS","color":"RED"}],"targetIdentifiers":["CUSTOM"]},"name":"Example target board name.","description":"Example target board description.","rid":"ri.gotham-artifact.0-0.target-board.example"}

### Error Responses

| name | description |
| --- | --- |
| InvalidClassificationPortionMarkings | The specified portion markings are not valid. |
| InvalidSpaceRid | The space rid is missing or invalid. |
| MultitenantModeUnknown | Multitenant mode is currently unknown. |
| CreateTargetBoardPermissionDenied | Could not create the TargetBoard. |
