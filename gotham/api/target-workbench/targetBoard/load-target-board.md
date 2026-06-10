---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench/targetBoard/load-target-board/"
title: "Load a Target Board \u2022 API Reference"
---
# Load a Target Board

## Endpoint

Load Target Board by RID.

**operationId:** v1.loadTargetBoardV2

**path:** /api/gotham/v1/twb/targetBoard/{rid}

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | Target Board RID |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Response

#### Body

Success response with the requested Target Board.

**name:** LoadTargetBoardResponseV2

**example:** {"rid":"ri.gotham-artifact.0-0.target-collection.example","name":"Example target board name.","description":"Example description.","highPriorityTargetList":"ri.gotham-artifact.0-0.hptl.example","configuration":{"columns":[{"id":"EXECUTION","name":"DONE","color":"RED"}],"targetIdentifiers":["CUSTOM"]},"targetColumnIds":{"bi.2a46fbf6-ff93-4710-951a-015ed5c92441*ri.gotham-artifact.0-0.target.1":{"columnId":"EXECUTION"},"bi.8a66fbf3-ff93-4710-951a-015ee5c92441*ri.gotham-artifact.0-0.target.2":{"columnId":"EXECUTION"}}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| targetBoard | objectType | True |  |
| baseRevisionId | stringType | True | The current version of the Collection retrieved. Any modifying operations should be accompanied by this version to avoid concurrent operations made since this version. If there are any conflicting edits that result in changes to these operations when they're applied, that will be noted in the response. |

**example:** {"rid":"ri.gotham-artifact.0-0.target-collection.example","name":"Example target board name.","description":"Example description.","highPriorityTargetList":"ri.gotham-artifact.0-0.hptl.example","configuration":{"columns":[{"id":"EXECUTION","name":"DONE","color":"RED"}],"targetIdentifiers":["CUSTOM"]},"targetColumnIds":{"bi.2a46fbf6-ff93-4710-951a-015ed5c92441*ri.gotham-artifact.0-0.target.1":{"columnId":"EXECUTION"},"bi.8a66fbf3-ff93-4710-951a-015ee5c92441*ri.gotham-artifact.0-0.target.2":{"columnId":"EXECUTION"}}}
