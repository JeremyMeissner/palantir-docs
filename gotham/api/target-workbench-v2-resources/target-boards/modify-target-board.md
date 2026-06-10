---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench-v2-resources/target-boards/modify-target-board/"
title: "Modify Target Board \u2022 API Reference"
---
# Modify Target Board

## Endpoint

Modify a Target Board by RID.

Sets the current state of a Collection. Any fields, except `hptl`, not supplied will result in
removal if there was a value present. Trying to set `hptl` to empty when there's already a value will
result in an INVALID_ARGUMENT exception. You cannot modify the `hptl` field if a value is already set.
Fields that are not supported by the OpenAPI layer will remain unmodified.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:target-write`.

**operationId:** v2.modifyTargetBoard

**path:** /api/v2/targetWorkbench/targetBoards/{targetBoardRid}/modify

### Operation Type

### Scopes

| name |
| --- |
| api:target-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| targetBoardRid | stringType | True | The unique identifier for a Target Board |

### Request

#### Body

**name:** ModifyTargetBoardRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| name | stringType | True |  |
| description | stringType | False |  |
| highPriorityTargetList | stringType | False |  |
| configuration | objectType | False | Configuration for a target board |
| baseRevisionId | stringType | True | The current version of the Target Board to be modified. The archive operation will be transformed against any concurrent operations made since this version. If there are any conflicting edits that result in changes to these operations when they're applied, that will be noted in the response. |

**example:** {"highPriorityTargetList":"ri.gotham-artifact.0-0.hptl.example","configuration":{"columns":[{"id":"EXECUTION","name":"IN PROGRESS","color":"RED"}],"targetIdentifiers":["CUSTOM"]},"name":"Example target board name.","description":"Example target board description.","baseRevisionId":1}

### Response

#### Body

An empty response object indicating the request was successful.

**name:** EmptySuccessResponse

### Error Responses

| name | description |
| --- | --- |
| CannotUpdateColumnsWithTargets | Cannot update a target board's columns if targets are present in the column. |
| RevisionOutdated | The provided revision id is behind the current id. |
| ModifyTargetBoardPermissionDenied | Could not modify the TargetBoard. |
