---
source_url: "https://www.palantir.com/docs/foundry/api/orchestration-v2-resources/schedules/get-affected-resources-schedule/"
title: "Get Affected Resources Schedule \u2022 API Reference"
---
# Get Affected Resources Schedule

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:orchestration-read`.

**operationId:** v2.getAffectedResourcesSchedule

**path:** /api/v2/orchestration/schedules/{scheduleRid}/getAffectedResources

### Operation Type

### Scopes

| name |
| --- |
| api:orchestration-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| scheduleRid | stringType | True | The RID of a Schedule. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** AffectedResourcesResponse

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| datasets | listType | False |  |

### Error Responses

| name | description |
| --- | --- |
| GetAffectedResourcesSchedulePermissionDenied | Could not getAffectedResources the Schedule. |
