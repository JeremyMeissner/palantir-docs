---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/object-types/get-object-type-edits-history/"
title: "Get Object Type Edits History \u2022 API Reference"
---
# Get Object Type Edits History

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Returns the history of edits (additions, modifications, deletions) for objects of a
specific object type. This endpoint provides visibility into all actions that have
modified objects of this type.

The edits are returned in reverse chronological order (most recent first) by default. 

Note that filters are ignored for OSv1 object types.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.getObjectTypeEditsHistory

**path:** /api/v2/ontologies/{ontology}/objectTypes/{objectType}/editsHistory

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The ontology RID or API name |
| objectType | stringType | True | The API name of the object type |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branch | stringType | False | The Foundry branch from which we will get edits history. If not specified, the default branch is used. Branches are an experimental feature and not all workflows are supported. |
| scenarioRid | stringType | False | The resource identifier of an ontology scenario to get edits history from. |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |

### Request

#### Body

Request object for querying object type edits history, containing both filters and pagination parameters

If objectPrimaryKey property is set, the method will return edits history for the particular object.
Otherwise, the method will return edits history for all objects of this object type.

**name:** ObjectTypeEditsHistoryRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| objectPrimaryKey | mapType | False |  |
| filters | unionType | False |  |
| sortOrder | enumType | False |  |
| includeAllPreviousProperties | booleanType | False |  |
| pageSize | integerType | False | The maximum number of edits to return per page. Defaults to 100. |
| pageToken | stringType | False | Token for retrieving the next page of results |

### Response

#### Body

Success response

**name:** ObjectTypeEditsHistoryResponse

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False | List of historical edits for this object type |
| totalCount | integerType | False | Count of items in the data array above |
| nextPageToken | stringType | False | Token for retrieving the next page of results |
