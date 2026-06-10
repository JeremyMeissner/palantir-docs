---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench/targetBoard/modify-target-board/"
title: "Modify a Target Board \u2022 API Reference"
---
# Modify a Target Board

## Endpoint

Modify a Target Board by RID.

**operationId:** v1.modifyTargetBoardV2

**path:** /api/gotham/v1/twb/targetBoard/{rid}

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | TargetBoard RID |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

The request body to modify the Target Board.

**name:** ModifyTargetBoardRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| name | stringType | True |  |
| description | stringType | False |  |
| highPriorityTargetList | stringType | False |  |
| configuration | objectType | False | Configuration for the target board. If present, must have at least one column |
| baseRevisionId | stringType | True | The current version of the Target Board to be modified. The archive operation will be transformed against any concurrent operations made since this version. If there are any conflicting edits that result in changes to these operations when they're applied, that will be noted in the response. |

**example:** {"name":"New example target board name","description":"New example description.","highPriorityTargetList":"ri.gotham-artifact.0-0.hptl.example","configuration":{"columns":[{"id":"EXECUTION","name":"IN PROGRESS","color":"RED"}],"targetIdentifiers":["CUSTOM"]},"targetColumnIds":{"bi.2a46fbf6-ff93-4710-951a-015ed5c92441*ri.gotham-artifact.0-0.target.1":{"columnId":"EXECUTION","customSortPriority":4},"bi.8a66fbf3-ff93-4710-951a-015ee5c92441*ri.gotham-artifact.0-0.target.2":{"columnId":"EXECUTION","customSortPriority":4}},"baseRevisionId":1}

### Response

#### Body

Success response

**name:** EmptySuccessResponse
