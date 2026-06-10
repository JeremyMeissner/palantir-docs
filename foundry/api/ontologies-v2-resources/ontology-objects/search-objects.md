---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/ontology-objects/search-objects/"
title: "Search Objects \u2022 API Reference"
---
# Search Objects

## Endpoint

Search for objects in the specified ontology and object type. The request body is used
to filter objects based on the specified query. The supported queries are:

| Query type                              | Description                                                                                                       | Supported Types                 |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------|---------------------------------|
| lt                                      | The provided property is less than the provided value.                                                            | number, string, date, timestamp |
| gt                                      | The provided property is greater than the provided value.                                                         | number, string, date, timestamp |
| lte                                     | The provided property is less than or equal to the provided value.                                                | number, string, date, timestamp |
| gte                                     | The provided property is greater than or equal to the provided value.                                             | number, string, date, timestamp |
| eq                                      | The provided property is exactly equal to the provided value.                                                     | number, string, date, timestamp |
| isNull                                  | The provided property is (or is not) null.                                                                        | all                             |
| contains                                | The provided property contains the provided value.                                                                | array                           |
| not                                     | The sub-query does not match.                                                                                     | N/A (applied on a query)        |
| and                                     | All the sub-queries match.                                                                                        | N/A (applied on queries)        |
| or                                      | At least one of the sub-queries match.                                                                            | N/A (applied on queries)        |
| containsAllTermsInOrderPrefixLastTerm   | The provided property contains all the terms provided in order. The last term can be a partial prefix match.      | string                          |
| containsAllTermsInOrder                 | The provided property contains the provided term as a substring.                                                  | string                          |
| containsAnyTerm                         | The provided property contains at least one of the terms separated by whitespace.                                 | string                          |
| containsAllTerms                        | The provided property contains all the terms separated by whitespace.                                             | string                          |
| startsWith                              | Deprecated alias for containsAllTermsInOrderPrefixLastTerm.                                                       | string                          |

Queries can be at most three levels deep. By default, terms are separated by whitespace or punctuation (`?!,:;-[](){}'"~`). Periods (`.`) on their own are ignored.
Partial terms are not matched by terms filters except where explicitly noted.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.searchObjectsV2

**path:** /api/v2/ontologies/{ontology}/objects/{objectType}/search

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The API name or RID of the Ontology. To find the API name or RID, use the **List Ontologies** endpoint or check the **Ontology Manager**. |
| objectType | stringType | True | The API name of the object type. To find the API name, use the **List object types** endpoint or check the **Ontology Manager**. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| sdkPackageRid | stringType | False | The package rid of the generated SDK. |
| sdkVersion | stringType | False | The version of the generated SDK. |
| branch | stringType | False | The Foundry branch to search objects from. If not specified, the default branch will be used. Branches are an experimental feature and not all workflows are supported. |
| executeInMemoryOnly | booleanType | False | If true, the request fails with an error when it cannot be computed in-memory. Use this to opt into fast failure on requests that would otherwise require heavier computation.  Defaults to false. |

### Request

#### Body

**name:** SearchObjectsRequestV2

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| where | unionType | False |  |
| orderBy | objectType | False | Specifies the ordering of search results by a field and an ordering direction or by relevance if scores are required in a nearestNeighbors query. By default `orderType` is set to `fields`. |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| select | listType | False | The API names of the object type properties to include in the response. |
| selectV2 | listType | False | The identifiers of the properties to include in the response. Only selectV2 or select should be populated, but not both. |
| excludeRid | booleanType | False | A flag to exclude the retrieval of the `__rid` property. Setting this to true may improve performance of this endpoint for object types in OSV2. |
| snapshot | booleanType | False | A flag to use snapshot consistency when paging. Setting this to true will give you a consistent view from before you start paging through the results, ensuring you do not get duplicate or missing items. Setting this to false will let new results enter as you page, but you may encounter duplicate or missing items. This defaults to false if not specified, which means you will always get the latest results. |

**example:** {"where":{"type":"eq","field":"age","value":21}}

### Response

#### Body

Success response.

**name:** SearchObjectsResponseV2

**example:** {"data":[{"__rid":"ri.phonograph2-objects.main.object.5b5dbc28-7f05-4e83-a33a-1e5b851ababb","__primaryKey":1000,"__apiName":"Employee","employeeId":1000,"lastName":"smith","firstName":"john","age":21}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| totalCount | stringType | True | The total number of items across all pages. |

**example:** {"data":[{"__rid":"ri.phonograph2-objects.main.object.5b5dbc28-7f05-4e83-a33a-1e5b851ababb","__primaryKey":1000,"__apiName":"Employee","employeeId":1000,"lastName":"smith","firstName":"john","age":21}]}
