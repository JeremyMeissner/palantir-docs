---
source_url: "https://www.palantir.com/docs/foundry/api/orchestration-v2-resources/schedules/delete-schedule/"
title: "Delete Schedule \u2022 API Reference"
---
# Delete Schedule

## Endpoint

Delete the Schedule with the specified rid.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:orchestration-write`.

**operationId:** v2.deleteSchedule

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

### Error Responses

| name | description |
| --- | --- |
| DeleteSchedulePermissionDenied | Could not delete the Schedule. |
