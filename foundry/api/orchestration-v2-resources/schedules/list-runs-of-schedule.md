---
source_url: "https://www.palantir.com/docs/foundry/api/orchestration-v2-resources/schedules/list-runs-of-schedule/"
title: "List Runs Of Schedule \u2022 API Reference"
---
# List Runs Of Schedule

## Endpoint

Get the most recent runs of a Schedule. If no page size is provided, a page size of 100 will be used.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:orchestration-read`.

**operationId:** v2.listRunsOfSchedule

**path:** /api/v2/orchestration/schedules/{scheduleRid}/runs

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
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

### Response

#### Body

**name:** ListRunsOfScheduleResponse

**example:** {"data":[{"scheduleVersionRid":"ri.scheduler.main.schedule-version.4d1eb55f-6c13-411c-a911-5d84e08d8017","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","scheduleRid":"ri.scheduler.main.schedule.5ad5c340-59f3-4a60-9fc6-161bb984f871","createdTime":"2003-05-06T12:34:56.789Z","rid":"ri.scheduler.main.run.d2a5e9c6-298d-4788-a71d-42885d7bebb3"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"scheduleVersionRid":"ri.scheduler.main.schedule-version.4d1eb55f-6c13-411c-a911-5d84e08d8017","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","scheduleRid":"ri.scheduler.main.schedule.5ad5c340-59f3-4a60-9fc6-161bb984f871","createdTime":"2003-05-06T12:34:56.789Z","rid":"ri.scheduler.main.run.d2a5e9c6-298d-4788-a71d-42885d7bebb3"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}
