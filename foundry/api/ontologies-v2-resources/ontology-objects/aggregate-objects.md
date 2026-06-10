---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/ontology-objects/aggregate-objects/"
title: "Aggregate Objects \u2022 API Reference"
---
# Aggregate Objects

## Endpoint

Perform functions on object fields in the specified ontology and object type.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.aggregateObjectsV2

**path:** /api/v2/ontologies/{ontology}/objects/{objectType}/aggregate

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The API name or RID of the Ontology. To find the API name or RID, use the **List Ontologies** endpoint or check the **Ontology Manager**. |
| objectType | stringType | True | The type of the object to aggregate on. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| sdkPackageRid | stringType | False | The package rid of the generated SDK. |
| sdkVersion | stringType | False | The version of the generated SDK. |
| branch | stringType | False | The Foundry branch to aggregate objects from. If not specified, the default branch will be used. Branches are an experimental feature and not all workflows are supported. |

### Request

#### Body

**name:** AggregateObjectsRequestV2

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| aggregation | listType | False |  |
| where | unionType | False |  |
| groupBy | listType | False |  |
| accuracy | enumType | False | Specifies the accuracy requirement for aggregation results.  - `REQUIRE_ACCURATE`: Only return results if they are guaranteed to be accurate. If accuracy cannot be   guaranteed (e.g., due to a low `maxGroupCount` relative to distinct values), the request will fail   with an `AggregationAccuracyNotSupported` error. - `ALLOW_APPROXIMATE`: Allow approximate results when exact computation is not feasible. This is the   default behavior if not specified. |

**example:** {"aggregation":[{"type":"min","field":"tenure","name":"min_tenure"},{"type":"avg","field":"tenure","name":"avg_tenure"}],"where":{"type":"eq","field":"name","value":"john"},"groupBy":[{"field":"startDate","type":"range","ranges":[{"startValue":"2020-01-01","endValue":"2020-06-01"}]},{"field":"city","type":"exact"}]}

### Response

#### Body

Success response.

**name:** AggregateObjectsResponseV2

**example:** {"data":[{"metrics":[{"name":"min_tenure","value":1},{"name":"avg_tenure","value":3}],"group":{"startDate":{"startValue":"2020-01-01","endValue":"2020-06-01"},"city":"New York City"}},{"metrics":[{"name":"min_tenure","value":2},{"name":"avg_tenure","value":3}],"group":{"startDate":{"startValue":"2020-01-01","endValue":"2020-06-01"},"city":"San Francisco"}}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| excludedItems | integerType | False |  |
| accuracy | enumType | True |  |
| data | listType | False |  |
| computeUsage | numberType | False | A measurement of compute usage expressed in [compute-seconds](/docs/foundry/resource-management/usage-types#compute-second). For more information, please refer to the [Usage types](/docs/foundry/resource-management/usage-types) documentation. |

**example:** {"data":[{"metrics":[{"name":"min_tenure","value":1},{"name":"avg_tenure","value":3}],"group":{"startDate":{"startValue":"2020-01-01","endValue":"2020-06-01"},"city":"New York City"}},{"metrics":[{"name":"min_tenure","value":2},{"name":"avg_tenure","value":3}],"group":{"startDate":{"startValue":"2020-01-01","endValue":"2020-06-01"},"city":"San Francisco"}}]}
