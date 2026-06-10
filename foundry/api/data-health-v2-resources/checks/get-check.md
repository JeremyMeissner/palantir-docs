---
source_url: "https://www.palantir.com/docs/foundry/api/data-health-v2-resources/checks/get-check/"
title: "Get Check \u2022 API Reference"
---
# Get Check

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Get the Check with the specified rid.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:data-health-read`.

**operationId:** v2.getCheck

**path:** /api/v2/dataHealth/checks/{checkRid}

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
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

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
| CheckTypeNotSupported | The type of the requested check is not yet supported in the Platform API. |
| CheckNotFound | The given Check could not be found. |
