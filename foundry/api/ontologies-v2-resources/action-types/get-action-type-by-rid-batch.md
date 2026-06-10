---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/action-types/get-action-type-by-rid-batch/"
title: "Get Action Type By Rid Batch \u2022 API Reference"
---
# Get Action Type By Rid Batch

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Gets a list of action types by RID in bulk.

Action types are filtered from the response if they don't exist or the requesting token lacks the required
permissions.

The maximum batch size for this endpoint is 100.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.getActionTypeByRidBatch

**path:** /api/v2/ontologies/{ontology}/actionTypes/getByRidBatch

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The API name or RID of the Ontology. To find the API name or RID, use the **List Ontologies** endpoint or check the **Ontology Manager**. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branch | stringType | False | The Foundry branch to load the action type definitions from. If not specified, the default branch will be used. Branches are an experimental feature and not all workflows are supported. |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |

### Request

#### Body

**name:** GetActionTypeByRidBatchRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| requests | listType | False |  |

### Response

#### Body

Success response.

**name:** GetActionTypeByRidBatchResponse

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
