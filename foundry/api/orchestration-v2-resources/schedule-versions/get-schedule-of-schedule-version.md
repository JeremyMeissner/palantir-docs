---
source_url: "https://www.palantir.com/docs/foundry/api/orchestration-v2-resources/schedule-versions/get-schedule-of-schedule-version/"
title: "Get Schedule Of Schedule Version \u2022 API Reference"
---
# Get Schedule Of Schedule Version

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:orchestration-read`.

**operationId:** v2.getScheduleOfScheduleVersion

**path:** /api/v2/orchestration/scheduleVersions/{scheduleVersionRid}/schedule

### Operation Type

### Scopes

| name |
| --- |
| api:orchestration-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| scheduleVersionRid | stringType | True | The RID of a schedule version |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** Schedule

**example:** {"updatedTime":"2024-09-25T17:29:35.974Z","paused":false,"updatedBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","displayName":"My Daily Schedule","currentVersionRid":"ri.scheduler.main.schedule-version.4d1eb55f-6c13-411c-a911-5d84e08d8017","description":"Run all the transforms at midnight","createdTime":"2024-09-25T17:29:35.974Z","action":{"abortOnFailure":false,"forceBuild":false,"retryBackoffDuration":{"unit":"SECONDS","value":30},"retryCount":1,"fallbackBranches":[],"branchName":"master","notificationsEnabled":false,"target":{"type":"manual","targetRids":["ri.foundry.main.dataset.b737e24d-6b19-43aa-93d5-da9fc4073f6e","ri.foundry.main.dataset.d2452a94-a755-4778-8bfc-a315ab52fc43"]}},"trigger":{"type":"time","cronExpression":"0 0 * * *","timeZone":"UTC"},"rid":"ri.scheduler.main.schedule.5ad5c340-59f3-4a60-9fc6-161bb984f871","scopeMode":{"type":"user"}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The RID of a Schedule. |
| displayName | stringType | False |  |
| description | stringType | False |  |
| currentVersionRid | stringType | True | The RID of the current schedule version |
| createdTime | stringType | True | The time at which the resource was created. |
| createdBy | stringType | True | The Foundry user who created this resource |
| updatedTime | stringType | True | The time at which the resource was most recently updated. |
| updatedBy | stringType | True | The Foundry user who last updated this resource |
| paused | booleanType | True |  |
| trigger | unionType | False | The schedule trigger. If the requesting user does not have permission to see the trigger, this will be empty. |
| action | objectType | True |  |
| scopeMode | unionType | True | The boundaries for the schedule build. |

**example:** {"updatedTime":"2024-09-25T17:29:35.974Z","paused":false,"updatedBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","displayName":"My Daily Schedule","currentVersionRid":"ri.scheduler.main.schedule-version.4d1eb55f-6c13-411c-a911-5d84e08d8017","description":"Run all the transforms at midnight","createdTime":"2024-09-25T17:29:35.974Z","action":{"abortOnFailure":false,"forceBuild":false,"retryBackoffDuration":{"unit":"SECONDS","value":30},"retryCount":1,"fallbackBranches":[],"branchName":"master","notificationsEnabled":false,"target":{"type":"manual","targetRids":["ri.foundry.main.dataset.b737e24d-6b19-43aa-93d5-da9fc4073f6e","ri.foundry.main.dataset.d2452a94-a755-4778-8bfc-a315ab52fc43"]}},"trigger":{"type":"time","cronExpression":"0 0 * * *","timeZone":"UTC"},"rid":"ri.scheduler.main.schedule.5ad5c340-59f3-4a60-9fc6-161bb984f871","scopeMode":{"type":"user"}}
