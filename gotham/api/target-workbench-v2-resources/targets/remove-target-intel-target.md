---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench-v2-resources/targets/remove-target-intel-target/"
title: "Remove Target Intel Target \u2022 API Reference"
---
# Remove Target Intel Target

## Endpoint

Remove Intel on Target by RID.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:target-write`.

**operationId:** v2.removeTargetIntelTarget

**path:** /api/v2/targetWorkbench/targets/{targetRid}/removeTargetIntel

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

**name:** RemoveTargetIntelTargetRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| id | stringType | True |  |

**example:** {"id":"Example Intel Id"}

### Response

#### Body

An empty response object indicating the request was successful.

**name:** EmptySuccessResponse

### Error Responses

| name | description |
| --- | --- |
| TargetNotFound | Cannot find target from provided rid. |
| RemoveTargetIntelTargetPermissionDenied | Could not removeTargetIntel the Target. |
