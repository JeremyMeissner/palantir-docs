---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench/target/archive-target/"
title: "Archive a Target \u2022 API Reference"
---
# Archive a Target

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Archive a Target by RID.
The user is required to have OWN permissions on the target.

**operationId:** v1.archiveTargetV2

**path:** /api/gotham/v1/twb/target/{rid}/archive

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | Target RID |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Response

#### Body

Success response.

**name:** EmptySuccessResponse
