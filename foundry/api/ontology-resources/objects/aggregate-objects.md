---
source_url: "https://www.palantir.com/docs/foundry/api/ontology-resources/objects/aggregate-objects/"
title: "Aggregate Objects \u2022 API Reference"
---
# Aggregate Objects

## Endpoint

Perform functions on object fields in the specified ontology and object type.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v1.aggregateObjects

**path:** /api/v1/ontologies/{ontologyRid}/objects/{objectType}/aggregate

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontologyRid | stringType | True | The unique Resource Identifier (RID) of the Ontology that contains the objects. |
| objectType | stringType | True | The type of the object to aggregate on. |

### Request

#### Body

**name:** AggregateObjectsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| aggregation | listType | False |  |
| query | unionType | False |  |
| groupBy | listType | False |  |

**example:** {"aggregation":[{"type":"min","field":"properties.tenure","name":"min_tenure"},{"type":"avg","field":"properties.tenure","name":"avg_tenure"}],"query":{"not":{"field":"properties.name","eq":"john"}},"groupBy":[{"field":"properties.startDate","type":"range","ranges":[{"gte":"2020-01-01","lt":"2020-06-01"}]},{"field":"properties.city","type":"exact"}]}

### Response

#### Body

Success response.

**name:** AggregateObjectsResponse

**example:** {"data":[{"metrics":[{"name":"min_tenure","value":1},{"name":"avg_tenure","value":3}],"group":{"properties.startDate":{"gte":"2020-01-01","lt":"2020-06-01"},"properties.city":"New York City"}},{"metrics":[{"name":"min_tenure","value":2},{"name":"avg_tenure","value":3}],"group":{"properties.startDate":{"gte":"2020-01-01","lt":"2020-06-01"},"properties.city":"San Francisco"}}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| excludedItems | integerType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| data | listType | False |  |

**example:** {"data":[{"metrics":[{"name":"min_tenure","value":1},{"name":"avg_tenure","value":3}],"group":{"properties.startDate":{"gte":"2020-01-01","lt":"2020-06-01"},"properties.city":"New York City"}},{"metrics":[{"name":"min_tenure","value":2},{"name":"avg_tenure","value":3}],"group":{"properties.startDate":{"gte":"2020-01-01","lt":"2020-06-01"},"properties.city":"San Francisco"}}]}
