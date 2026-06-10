---
source_url: "https://www.palantir.com/docs/foundry/api/data-health-v2-resources/checks/create-check/"
title: "Create Check \u2022 API Reference"
---
# Create Check

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Creates a new Check.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:data-health-write`.

**operationId:** v2.createCheck

**path:** /api/v2/dataHealth/checks

### Operation Type

### Scopes

| name |
| --- |
| api:data-health-write |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** CreateCheckRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| config | unionType | True | Configuration of a check. |
| intent | stringType | False | A note about why the Check was set up. |

**example:** {"intent":"Check to ensure builds are passing."}

### Response

#### Body

The created Check

**name:** Check

**example:** {"updatedTime":"2024-09-25T17:29:35.974Z","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","groups":["ri.data-health.main.check-group.08e376a8-607d-4f44-b8dd-b4587be6ce9b"],"rid":"ri.data-health.main.check.8e27b13a-e21b-4232-ae1b-76ccf5ff42b3","intent":"Check to ensure builds are passing."}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The unique resource identifier (RID) of a Data Health Check. |
| groups | listType | False |  |
| config | unionType | True | Configuration of a check. |
| intent | stringType | False | A note about why the Check was set up. |
| createdBy | stringType | False | The user that created the Check. |
| updatedTime | stringType | False | The timestamp when the Check was last updated. |

**example:** {"updatedTime":"2024-09-25T17:29:35.974Z","createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","groups":["ri.data-health.main.check-group.08e376a8-607d-4f44-b8dd-b4587be6ce9b"],"rid":"ri.data-health.main.check.8e27b13a-e21b-4232-ae1b-76ccf5ff42b3","intent":"Check to ensure builds are passing."}

### Error Responses

| name | description |
| --- | --- |
| CheckAlreadyExists | A check of the given type for the given subject(s) already exists. The conflicting check will be returned if the provided token has permission to view it. |
| InvalidTimeCheckConfig | The TimeCheckConfig is invalid. It must contain at least one of timeBounds or medianDeviation. |
| InvalidPercentageCheckConfig | The PercentageCheckConfig is invalid. It must contain at least one of percentageBounds or medianDeviation. |
| InvalidNumericColumnCheckConfig | The NumericColumnCheckConfig is invalid. It must contain at least one of numericBounds or trend. |
| InvalidTrendConfig | The TrendConfig is invalid. It must contain at least one of trendType or differenceBounds. |
| InvalidTransactionTimeCheckConfig | The TransactionTimeCheckConfig is invalid. It must contain at least one of timeBounds or medianDeviation. |
| CheckTypeNotSupported | The type of the requested check is not yet supported in the Platform API. |
| CreateCheckPermissionDenied | Could not create the Check. |
