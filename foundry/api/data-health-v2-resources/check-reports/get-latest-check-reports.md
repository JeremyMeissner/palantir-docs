---
source_url: "https://www.palantir.com/docs/foundry/api/data-health-v2-resources/check-reports/get-latest-check-reports/"
title: "Get Latest Check Reports \u2022 API Reference"
---
# Get Latest Check Reports

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Get the most recent check reports for this Check. Reports are returned
in reverse chronological order (most recent first).

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:data-health-read`.

**operationId:** v2.getLatestCheckReports

**path:** /api/v2/dataHealth/checks/{checkRid}/checkReports/getLatest

### Operation Type

### Scopes

| name |
| --- |
| api:data-health-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| checkRid | stringType | True | The unique resource identifier (RID) of a Data Health Check. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| limit | integerType | False | The maximum number of check reports to return. Defaults to 10. Maximum allowed value is 100. |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

The response for getting the latest check reports.

**name:** GetLatestCheckReportsResponse

**example:** {"data":[{"result":{"status":"PASSED"},"createdTime":"2003-05-06T12:34:56.789Z","check":{"updatedTime":"2024-09-25T17:29:35.974Z","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","groups":["ri.data-health.main.check-group.08e376a8-607d-4f44-b8dd-b4587be6ce9b"],"rid":"ri.data-health.main.check.8e27b13a-e21b-4232-ae1b-76ccf5ff42b3","intent":"Check to ensure builds are passing."},"rid":"ri.data-health.main.check-report.a1b2c3d4-e5f6-7890-abcd-ef1234567890"}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False | The list of check reports. |

**example:** {"data":[{"result":{"status":"PASSED"},"createdTime":"2003-05-06T12:34:56.789Z","check":{"updatedTime":"2024-09-25T17:29:35.974Z","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","groups":["ri.data-health.main.check-group.08e376a8-607d-4f44-b8dd-b4587be6ce9b"],"rid":"ri.data-health.main.check.8e27b13a-e21b-4232-ae1b-76ccf5ff42b3","intent":"Check to ensure builds are passing."},"rid":"ri.data-health.main.check-report.a1b2c3d4-e5f6-7890-abcd-ef1234567890"}]}

### Error Responses

| name | description |
| --- | --- |
| CheckTypeNotSupported | The type of the requested check is not yet supported in the Platform API. |
| GetLatestCheckReportsPermissionDenied | Could not getLatest the CheckReport. |
| CheckNotFound | The given Check could not be found. |
