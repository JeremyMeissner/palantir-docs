---
source_url: "https://www.palantir.com/docs/foundry/api/orchestration-v2-resources/schedules/replace-schedule/"
title: "Replace Schedule \u2022 API Reference"
---
# Replace Schedule

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Replaces the Schedule with the specified rid.

:::callout{theme=warning title=Warning}
If the schedule is configured in user-scoped mode, outputs to build will be discovered based on resources
that the user has access to. If the user's permissions change later, this could change the outputs that
will be built or cause builds to fail. Consider using a project-scoped schedule instead.
:::

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:orchestration-write`.

**operationId:** v2.replaceSchedule

**path:** /api/v2/orchestration/schedules/{scheduleRid}

### Operation Type

### Scopes

| name |
| --- |
| api:orchestration-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| scheduleRid | stringType | True | The RID of a Schedule. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** ReplaceScheduleRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| displayName | stringType | False |  |
| description | stringType | False |  |
| action | objectType | True |  |
| trigger | unionType | False | The schedule trigger. If the requesting user does not have permission to see the trigger, this will be empty. |
| scopeMode | unionType | False | The boundaries for the schedule build. |

**example:** {"displayName":"My Daily Schedule","description":"Run all the transforms at midnight","action":{"abortOnFailure":false,"forceBuild":false,"retryBackoffDuration":{"unit":"SECONDS","value":30},"retryCount":1,"fallbackBranches":[],"branchName":"master","notificationsEnabled":false,"target":{"type":"manual","targetRids":["ri.foundry.main.dataset.b737e24d-6b19-43aa-93d5-da9fc4073f6e","ri.foundry.main.dataset.d2452a94-a755-4778-8bfc-a315ab52fc43"]}},"trigger":{"type":"time","cronExpression":"0 0 * * *","timeZone":"UTC"},"scopeMode":{"type":"user"}}

### Response

#### Body

The replaced Schedule

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

### Error Responses

| name | description |
| --- | --- |
| ReplaceSchedulePermissionDenied | Could not replace the Schedule. |
