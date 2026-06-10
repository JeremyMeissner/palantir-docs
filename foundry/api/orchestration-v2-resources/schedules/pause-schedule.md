---
source_url: "https://www.palantir.com/docs/foundry/api/orchestration-v2-resources/schedules/pause-schedule/"
title: "Pause Schedule \u2022 API Reference"
---
# Pause Schedule

## Endpoint

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:orchestration-write`.

**operationId:** v2.pauseSchedule

**path:** /api/v2/orchestration/schedules/{scheduleRid}/pause

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
| PauseSchedulePermissionDenied | Could not pause the Schedule. |
