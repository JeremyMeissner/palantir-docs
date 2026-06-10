---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/object-types/get-outgoing-link-types-by-object-type-rid-batch/"
title: "Get Outgoing Link Types By Object Type Rid Batch \u2022 API Reference"
---
# Get Outgoing Link Types By Object Type Rid Batch

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Gets outgoing link types for a batch of object types, identified by their RIDs.

For each requested object type, returns the list of outgoing link types visible to the
requesting token. Optionally, results can be filtered to only include specific link type RIDs.

Object types that don't exist or that the requesting token lacks permissions for are
silently omitted from the response.

The maximum batch size for this endpoint is 100.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.getOutgoingLinkTypesByObjectTypeRidBatch

**path:** /api/v2/ontologies/{ontology}/outgoingLinkTypes/getByRidBatch

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
| branch | stringType | False | The Foundry branch to load the outgoing link type definitions from. If not specified, the default branch will be used. Branches are an experimental feature and not all workflows are supported. |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |

### Request

#### Body

**name:** GetOutgoingLinkTypesByObjectTypeRidBatchRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| requests | listType | False |  |
| filterLinkTypeRids | listType | False | If provided, only return outgoing link types with RIDs in this list. If omitted, all outgoing link types for each requested object type are returned. |

### Response

#### Body

Success response.

**name:** GetOutgoingLinkTypesByObjectTypeRidBatchResponse

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | mapType | False |  |
