---
source_url: "https://www.palantir.com/docs/foundry/api/orchestration-v2-resources/schedules/get-schedules-batch/"
title: "Get Schedules Batch \u2022 API Reference"
---
# Get Schedules Batch

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Fetch multiple schedules in a single request. Schedules not found or inaccessible to the user will be 
omitted from the response.

The maximum batch size for this endpoint is 1000.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:orchestration-read`.

**operationId:** v2.getSchedulesBatch

**path:** /api/v2/orchestration/schedules/getBatch

### Operation Type

### Scopes

| name |
| --- |
| api:orchestration-read |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** body

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| GetSchedulesBatchRequestElement | objectType | True |  |

**example:** [{"scheduleRid":"ri.scheduler.main.schedule.5ad5c340-59f3-4a60-9fc6-161bb984f871"}]

### Response

#### Body

**name:** GetSchedulesBatchResponse

**example:** {"data":{"ri.scheduler.main.schedule.5ad5c340-59f3-4a60-9fc6-161bb984f871":{"updatedTime":"2024-09-25T17:29:35.974Z","paused":false,"updatedBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","displayName":"My Daily Schedule","currentVersionRid":"ri.scheduler.main.schedule-version.4d1eb55f-6c13-411c-a911-5d84e08d8017","description":"Run all the transforms at midnight","createdTime":"2024-09-25T17:29:35.974Z","action":{"abortOnFailure":false,"forceBuild":false,"retryBackoffDuration":{"unit":"SECONDS","value":30},"retryCount":1,"fallbackBranches":[],"branchName":"master","notificationsEnabled":false,"target":{"type":"manual","targetRids":["ri.foundry.main.dataset.b737e24d-6b19-43aa-93d5-da9fc4073f6e","ri.foundry.main.dataset.d2452a94-a755-4778-8bfc-a315ab52fc43"]}},"trigger":{"type":"time","cronExpression":"0 0 * * *","timeZone":"UTC"},"rid":"ri.scheduler.main.schedule.5ad5c340-59f3-4a60-9fc6-161bb984f871","scopeMode":{"type":"user"}}}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | mapType | False |  |

**example:** {"data":{"ri.scheduler.main.schedule.5ad5c340-59f3-4a60-9fc6-161bb984f871":{"updatedTime":"2024-09-25T17:29:35.974Z","paused":false,"updatedBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","displayName":"My Daily Schedule","currentVersionRid":"ri.scheduler.main.schedule-version.4d1eb55f-6c13-411c-a911-5d84e08d8017","description":"Run all the transforms at midnight","createdTime":"2024-09-25T17:29:35.974Z","action":{"abortOnFailure":false,"forceBuild":false,"retryBackoffDuration":{"unit":"SECONDS","value":30},"retryCount":1,"fallbackBranches":[],"branchName":"master","notificationsEnabled":false,"target":{"type":"manual","targetRids":["ri.foundry.main.dataset.b737e24d-6b19-43aa-93d5-da9fc4073f6e","ri.foundry.main.dataset.d2452a94-a755-4778-8bfc-a315ab52fc43"]}},"trigger":{"type":"time","cronExpression":"0 0 * * *","timeZone":"UTC"},"rid":"ri.scheduler.main.schedule.5ad5c340-59f3-4a60-9fc6-161bb984f871","scopeMode":{"type":"user"}}}}
