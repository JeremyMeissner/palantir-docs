---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/datasets/get-dataset-health-checks/"
title: "Get Dataset Health Checks \u2022 API Reference"
---
# Get Dataset Health Checks

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Get the RIDs of the Data Health Checks that are configured for the given Dataset.

Third-party applications using this endpoint via OAuth2 must request the following operation scopes: `api:data-health-read api:datasets-read`.

**operationId:** v2.getDatasetHealthChecks

**path:** /api/v2/datasets/{datasetRid}/getHealthChecks

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

**name:** ListHealthChecksResponse

**example:** {"data":["ri.data-health.main.check.8e27b13a-e21b-4232-ae1b-76ccf5ff42b3"]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |

**example:** {"data":["ri.data-health.main.check.8e27b13a-e21b-4232-ae1b-76ccf5ff42b3"]}

### Error Responses

| name | description |
| --- | --- |
| BranchNotFound | The requested branch could not be found, or the client token does not have access to it. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
| GetDatasetHealthChecksPermissionDenied | Could not getHealthChecks the Dataset. |
