---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench/intel/remove-target-intel/"
title: "Remove Intel From a Target \u2022 API Reference"
---
# Remove Intel From a Target

## Endpoint

Remove Intel on Target by RID

**operationId:** v1.removeTargetIntelV2

**path:** /api/gotham/v1/twb/removeTargetIntel/{rid}

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | Target RID |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

Request body to remove intel from situation based on ID.

**name:** RemoveTargetIntelRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| id | stringType | True |  |

**example:** {"id":"Example Intel Id"}

### Response

#### Body

Success response.

**name:** EmptySuccessResponse
