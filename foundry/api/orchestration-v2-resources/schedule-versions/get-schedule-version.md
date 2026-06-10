---
source_url: "https://www.palantir.com/docs/foundry/api/orchestration-v2-resources/schedule-versions/get-schedule-version/"
title: "Get Schedule Version \u2022 API Reference"
---
# Get Schedule Version

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Get the ScheduleVersion with the specified rid.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:orchestration-read`.

**operationId:** v2.getScheduleVersion

**path:** /api/v2/orchestration/scheduleVersions/{scheduleVersionRid}

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

**name:** ScheduleVersion

**example:** {"createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","scheduleRid":"ri.scheduler.main.schedule.5ad5c340-59f3-4a60-9fc6-161bb984f871","createdTime":"2003-05-06T12:34:56.789Z","action":{"abortOnFailure":false,"forceBuild":false,"retryBackoffDuration":{"unit":"SECONDS","value":30},"retryCount":1,"fallbackBranches":[],"branchName":"master","notificationsEnabled":false,"target":{"type":"manual","targetRids":["ri.foundry.main.dataset.b737e24d-6b19-43aa-93d5-da9fc4073f6e","ri.foundry.main.dataset.d2452a94-a755-4778-8bfc-a315ab52fc43"]}},"trigger":{"type":"time","cronExpression":"0 0 * * *","timeZone":"UTC"},"rid":"ri.scheduler.main.schedule-version.4d1eb55f-6c13-411c-a911-5d84e08d8017","scopeMode":{"type":"user"}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The RID of a schedule version |
| scheduleRid | stringType | True | The RID of a Schedule. |
| createdTime | stringType | True | The time the schedule version was created |
| createdBy | stringType | True | The Foundry user who created the schedule version |
| trigger | unionType | False |  |
| action | objectType | True |  |
| scopeMode | unionType | True | The boundaries for the schedule build. |

**example:** {"createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","scheduleRid":"ri.scheduler.main.schedule.5ad5c340-59f3-4a60-9fc6-161bb984f871","createdTime":"2003-05-06T12:34:56.789Z","action":{"abortOnFailure":false,"forceBuild":false,"retryBackoffDuration":{"unit":"SECONDS","value":30},"retryCount":1,"fallbackBranches":[],"branchName":"master","notificationsEnabled":false,"target":{"type":"manual","targetRids":["ri.foundry.main.dataset.b737e24d-6b19-43aa-93d5-da9fc4073f6e","ri.foundry.main.dataset.d2452a94-a755-4778-8bfc-a315ab52fc43"]}},"trigger":{"type":"time","cronExpression":"0 0 * * *","timeZone":"UTC"},"rid":"ri.scheduler.main.schedule-version.4d1eb55f-6c13-411c-a911-5d84e08d8017","scopeMode":{"type":"user"}}

### Error Responses

| name | description |
| --- | --- |
| ScheduleVersionNotFound | The given ScheduleVersion could not be found. |
