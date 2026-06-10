---
source_url: "https://www.palantir.com/docs/foundry/api/orchestration-v2-resources/schedules/unpause-schedule/"
title: "Unpause Schedule \u2022 API Reference"
---
# Unpause Schedule

## Endpoint

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:orchestration-write`.

**operationId:** v2.unpauseSchedule

**path:** /api/v2/orchestration/schedules/{scheduleRid}/unpause

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
| UnpauseSchedulePermissionDenied | Could not unpause the Schedule. |
