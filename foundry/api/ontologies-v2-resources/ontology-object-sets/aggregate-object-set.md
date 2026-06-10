---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/ontology-object-sets/aggregate-object-set/"
title: "Aggregate Object Set \u2022 API Reference"
---
# Aggregate Object Set

## Endpoint

Aggregates the ontology objects present in the `ObjectSet` from the provided object set definition.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.aggregateObjectSetV2

**path:** /api/v2/ontologies/{ontology}/objectSets/aggregate

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
| sdkPackageRid | stringType | False | The package rid of the generated SDK. |
| sdkVersion | stringType | False | The package version of the generated SDK. |
| branch | stringType | False | The Foundry branch to aggregate the objects from. If not specified, the default branch is used. Branches are an experimental feature and not all workflows are supported. |
| transactionId | stringType | False | The ID of an Ontology transaction to read from. Transactions are an experimental feature and all workflows may not be supported. |
| scenarioRid | stringType | False | The resource identifier of an ontology scenario to aggregate the objects on. |
| executeInMemoryOnly | booleanType | False | If true, the request fails with an error when it cannot be computed in-memory. Use this to opt into fast failure on requests that would otherwise require heavier computation.  Defaults to false. |

### Request

#### Body

**name:** AggregateObjectSetRequestV2

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| aggregation | listType | False |  |
| objectSet | unionType | True | Represents the definition of an `ObjectSet` in the `Ontology`. |
| groupBy | listType | False |  |
| accuracy | enumType | False | Specifies the accuracy requirement for aggregation results.  - `REQUIRE_ACCURATE`: Only return results if they are guaranteed to be accurate. If accuracy cannot be   guaranteed (e.g., due to a low `maxGroupCount` relative to distinct values), the request will fail   with an `AggregationAccuracyNotSupported` error. - `ALLOW_APPROXIMATE`: Allow approximate results when exact computation is not feasible. This is the   default behavior if not specified. |
| includeComputeUsage | booleanType | False | Indicates whether the response should include compute usage details for the request. This feature is currently only available for OSDK applications. Note: Enabling this flag may slow down query performance and is not recommended for use in production. |

**example:** {"objectSet":{"objectType":"Employee","type":"base"},"aggregation":[{"field":"tenure","name":"min_tenure","type":"min"},{"field":"tenure","name":"avg_tenure","type":"avg"}],"groupBy":[{"field":"startDate","ranges":[{"endValue":"2020-06-01","startValue":"2020-01-01"}],"type":"range"},{"field":"city","type":"exact"}]}

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
