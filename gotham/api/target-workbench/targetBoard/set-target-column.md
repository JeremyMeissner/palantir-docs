---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench/targetBoard/set-target-column/"
title: "Set the Target On a Column \u2022 API Reference"
---
# Set the Target On a Column

## Endpoint

Move a Target into a TargetBoardColumn from an old column.

**operationId:** v1.setTargetColumnV2

**path:** /api/gotham/v1/twb/setTargetColumn/{targetRid}

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| targetRid | stringType | True |  |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

Move a Target into a TargetBoardColumn, either from an old column or no column (newly created Target).

**name:** SetTargetColumnRequestV2

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| boardRid | stringType | True | The unique resource identifier of a Target Board. This is equivalent to a collection RID. |
| newColumnId | stringType | True | Equivalent to a collection column ID. The ID of a TargetCollectionColumn, default values are: DRAFT (Identified target), PLAN_DEVELOPMENT (Prioritized target), PLANNED (In coordination), EXECUTION (In execution), CLOSED (Complete). |
| baseRevisionId | stringType | True | The version of Target Board you are working with. The set operation will be transformed against any concurrent operations made since this version. If there are any conflicting edits that result in changes to these operations when they're applied, that will be noted in the response. |
| clientId | stringType | False | The client id is used to identify conflicting edits made by the same client, typically due to retries, and discard them. Clients should choose an arbitrary random identifier to distinguish themselves. There is no need persist and re-use the same client id over multiple sessions.  The client id is also used to avoid broadcasting operations to the client who submitted them. |

**example:** {"boardRid":"ri.gotham-artifact.0-0.target-board.example","newColumnId":"CLOSED"}

### Response

#### Body

Success response.

**name:** EmptySuccessResponse
