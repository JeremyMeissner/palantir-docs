---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench-v2-resources/targets/set-target-column-target/"
title: "Set Target Column Target \u2022 API Reference"
---
# Set Target Column Target

## Endpoint

Move a Target into a TargetBoardColumn from an old column.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:target-write`.

**operationId:** v2.setTargetColumnTarget

**path:** /api/v2/targetWorkbench/targets/{targetRid}/setTargetColumn

### Operation Type

### Scopes

| name |
| --- |
| api:target-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| targetRid | stringType | True | The unique identifier for a Target |

### Request

#### Body

**name:** SetTargetColumnTargetRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| boardRid | stringType | True | The unique identifier for a Target Board |
| newColumnId | stringType | True | Equivalent to a collection column ID. The ID of a TargetCollectionColumn, default values are: DRAFT (Identified target), PLAN_DEVELOPMENT (Prioritized target), PLANNED (In coordination), EXECUTION (In execution), CLOSED (Complete). |
| baseRevisionId | stringType | True | The version of Target Board you are working with. The set operation will be transformed against any concurrent operations made since this version. If there are any conflicting edits that result in changes to these operations when they're applied, that will be noted in the response. |
| clientId | stringType | False | The client id is used to identify conflicting edits made by the same client, typically due to retries, and discard them. Clients should choose an arbitrary random identifier to distinguish themselves. There is no need persist and re-use the same client id over multiple sessions.  The client id is also used to avoid broadcasting operations to the client who submitted them. |

**example:** {"clientId":"123e4567-e89b-12d3-a456-426614174000","boardRid":"ri.gotham-artifact.0-0.target-board.example","baseRevisionId":1,"newColumnId":"CLOSED"}

### Response

#### Body

An empty response object indicating the request was successful.

**name:** EmptySuccessResponse

### Error Responses

| name | description |
| --- | --- |
| TargetNotOnTargetBoard | Target must be located on the request target board. |
| RevisionOutdated | The provided revision id is behind the current id. |
| SetTargetColumnTargetPermissionDenied | Could not setTargetColumn the Target. |
