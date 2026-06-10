---
source_url: "https://www.palantir.com/docs/foundry/api/ontology-resources/objects/search-objects/"
title: "Search Objects \u2022 API Reference"
---
# Search Objects

## Endpoint

Search for objects in the specified ontology and object type. The request body is used
to filter objects based on the specified query. The supported queries are:

| Query type            | Description                                                                       | Supported Types                 |
|----------|-----------------------------------------------------------------------------------|---------------------------------|
| lt       | The provided property is less than the provided value.                            | number, string, date, timestamp |
| gt       | The provided property is greater than the provided value.                         | number, string, date, timestamp |
| lte      | The provided property is less than or equal to the provided value.                | number, string, date, timestamp |
| gte      | The provided property is greater than or equal to the provided value.             | number, string, date, timestamp |
| eq       | The provided property is exactly equal to the provided value.                     | number, string, date, timestamp |
| isNull   | The provided property is (or is not) null.                                        | all                             |
| contains | The provided property contains the provided value.                                | array                           |
| not      | The sub-query does not match.                                                     | N/A (applied on a query)        |
| and      | All the sub-queries match.                                                        | N/A (applied on queries)        |
| or       | At least one of the sub-queries match.                                            | N/A (applied on queries)        |
| prefix   | The provided property starts with the provided term.                              | string                          |
| phrase   | The provided property contains the provided term as a substring.                  | string                          |
| anyTerm  | The provided property contains at least one of the terms separated by whitespace. | string                          |
| allTerms | The provided property contains all the terms separated by whitespace.             | string                          |

Queries can be at most three levels deep. By default, terms are separated by whitespace or punctuation (`?!,:;-[](){}'"~`). Periods (`.`) on their own are ignored.
Partial terms are not matched by terms filters except where explicitly noted.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v1.searchObjects

**path:** /api/v1/ontologies/{ontologyRid}/objects/{objectType}/search

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontologyRid | stringType | True | The unique Resource Identifier (RID) of the Ontology that contains the objects. |
| objectType | stringType | True | The type of the requested objects. |

### Request

#### Body

**name:** SearchObjectsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| query | unionType | True |  |
| orderBy | objectType | False | Specifies the ordering of search results by a field and an ordering direction. |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| fields | listType | False | The API names of the object type properties to include in the response. |

**example:** {"query":{"not":{"field":"properties.age","eq":21}}}

### Response

#### Body

Success response.

**name:** SearchObjectsResponse

**example:** {"data":[{"properties":{"lastName":"smith","firstName":"john","age":21},"rid":"ri.phonograph2-objects.main.object.5b5dbc28-7f05-4e83-a33a-1e5b851ababb"}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| totalCount | stringType | True | The total number of items across all pages. |

**example:** {"data":[{"properties":{"lastName":"smith","firstName":"john","age":21},"rid":"ri.phonograph2-objects.main.object.5b5dbc28-7f05-4e83-a33a-1e5b851ababb"}]}
