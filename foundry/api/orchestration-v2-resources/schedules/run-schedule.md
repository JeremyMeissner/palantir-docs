---
source_url: "https://www.palantir.com/docs/foundry/api/orchestration-v2-resources/schedules/run-schedule/"
title: "Run Schedule \u2022 API Reference"
---
# Run Schedule

## Endpoint

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:orchestration-write`.

**operationId:** v2.runSchedule

**path:** /api/v2/orchestration/schedules/{scheduleRid}/run

### Operation Type

### Scopes

| name |
| --- |
| api:orchestration-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| scheduleRid | stringType | True | The RID of a Schedule. |

### Response

#### Body

**name:** ScheduleRun

**example:** {"scheduleVersionRid":"ri.scheduler.main.schedule-version.4d1eb55f-6c13-411c-a911-5d84e08d8017","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","scheduleRid":"ri.scheduler.main.schedule.5ad5c340-59f3-4a60-9fc6-161bb984f871","createdTime":"2003-05-06T12:34:56.789Z","rid":"ri.scheduler.main.run.d2a5e9c6-298d-4788-a71d-42885d7bebb3"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The RID of a schedule run |
| scheduleRid | stringType | True | The RID of a Schedule. |
| scheduleVersionRid | stringType | True | The RID of a schedule version |
| createdTime | stringType | True | The time at which the schedule run was created. |
| createdBy | stringType | False | The Foundry user who manually invoked this schedule run. Automatic trigger runs have this field set to empty. |
| result | unionType | False | The result of triggering the schedule. If empty, it means the service is still working on triggering the schedule. |

**example:** {"scheduleVersionRid":"ri.scheduler.main.schedule-version.4d1eb55f-6c13-411c-a911-5d84e08d8017","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","scheduleRid":"ri.scheduler.main.schedule.5ad5c340-59f3-4a60-9fc6-161bb984f871","createdTime":"2003-05-06T12:34:56.789Z","rid":"ri.scheduler.main.run.d2a5e9c6-298d-4788-a71d-42885d7bebb3"}

### Error Responses

| name | description |
| --- | --- |
| RunSchedulePermissionDenied | Could not run the Schedule. |
