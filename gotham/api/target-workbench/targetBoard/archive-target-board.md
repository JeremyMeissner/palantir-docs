---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench/targetBoard/archive-target-board/"
title: "Archive a Target Board \u2022 API Reference"
---
# Archive a Target Board

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Archive a Collection by RID.

**operationId:** v1.archiveTargetBoardV2

**path:** /api/gotham/v1/twb/targetBoard/{rid}/archive

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

Success response

**name:** EmptySuccessResponse
