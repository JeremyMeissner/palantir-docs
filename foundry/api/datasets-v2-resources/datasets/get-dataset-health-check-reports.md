---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/datasets/get-dataset-health-check-reports/"
title: "Get Dataset Health Check Reports \u2022 API Reference"
---
# Get Dataset Health Check Reports

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Get the most recent Data Health Check report for each check configured on the given Dataset.
Returns one report per check, representing the current health status of the dataset.

To get the list of checks configured on a Dataset, use
[Get Dataset Health Checks](/docs/foundry/api/datasets/get-dataset-health-checks/).
For the full report history of a specific check, use
[Get Latest Check Reports](/docs/foundry/api/v2/data-health-v2-resources/checks/get-latest-check-reports).

Third-party applications using this endpoint via OAuth2 must request the following operation scopes: `api:data-health-read api:datasets-read`.

**operationId:** v2.getDatasetHealthCheckReports

**path:** /api/v2/datasets/{datasetRid}/getHealthCheckReports

### Operation Type

### Scopes

| name |
| --- |
| api:data-health-read |
| api:datasets-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of a Dataset. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branchName | stringType | False | The name of the Branch. If none is provided, the default Branch name - `master` for most enrollments - will be used. |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** GetHealthCheckReportsResponse

**example:** {"data":{"ri.data-health.main.check.8e27b13a-e21b-4232-ae1b-76ccf5ff42b3":{"result":{"status":"PASSED"},"createdTime":"2003-05-06T12:34:56.789Z","check":{"updatedTime":"2024-09-25T17:29:35.974Z","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","groups":["ri.data-health.main.check-group.08e376a8-607d-4f44-b8dd-b4587be6ce9b"],"rid":"ri.data-health.main.check.8e27b13a-e21b-4232-ae1b-76ccf5ff42b3","intent":"Check to ensure builds are passing."},"rid":"ri.data-health.main.check-report.a1b2c3d4-e5f6-7890-abcd-ef1234567890"}}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | mapType | False | A map from Check RID to the most recent report for that check. If a check is configured but has not yet produced a report, the value will be absent. |

**example:** {"data":{"ri.data-health.main.check.8e27b13a-e21b-4232-ae1b-76ccf5ff42b3":{"result":{"status":"PASSED"},"createdTime":"2003-05-06T12:34:56.789Z","check":{"updatedTime":"2024-09-25T17:29:35.974Z","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","groups":["ri.data-health.main.check-group.08e376a8-607d-4f44-b8dd-b4587be6ce9b"],"rid":"ri.data-health.main.check.8e27b13a-e21b-4232-ae1b-76ccf5ff42b3","intent":"Check to ensure builds are passing."},"rid":"ri.data-health.main.check-report.a1b2c3d4-e5f6-7890-abcd-ef1234567890"}}}

### Error Responses

| name | description |
| --- | --- |
| BranchNotFound | The requested branch could not be found, or the client token does not have access to it. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
| CheckTypeNotSupported | The type of the requested check is not yet supported in the Platform API. |
| GetDatasetHealthCheckReportsPermissionDenied | Could not getHealthCheckReports the Dataset. |
