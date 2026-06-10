---
source_url: "https://www.palantir.com/docs/gotham/api/revdb-resources/objects/search-objects/"
title: "Search objects \u2022 API Reference"
---
# Search objects

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Search for objects of the given object type. The request body is used
to filter objects based on the specified query. The supported queries are:

| Query type      | Description                                                                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------- |
| `empty`         | Apply no filter (i.e., list all objects of type objectType).                                                                                  |
| `eq`            | Filter objects that have the exact value for the provided property                                                                            |
| `and`           | Filter objects that match all the provided queries                                                                                            |
| `or`            | Filter objects that match at least one of the provided queries                                                                                |
| `keyword`       | The objects' contents match the specified keyword query                                                                                       |
| `lt`            | Filter objects where the provided property is less than the provided value                                                                    |
| `gt`            | Filter objects where the provided property is greater than the provided value                                                                 |
| `lte`           | Filter objects where the provided property is less than or equal to the provided value                                                        |
| `gte`           | Filter objects where the provided property is greater than or equal to the provided value                                                     |
| `not`           | Filter objects that do not match the provided query                                                                                           |
| `geoPointWithin`| Filter objects whose intrinsic coordinates are within the provided polygon                                                                    |

For more details about available queries,
see [search query types](/docs/gotham/api/revdb-resources/objects/object-basics/#search-query-types).

**operationId:** v1.searchObjects

**path:** /api/gotham/v1/objects/types/{objectType}/search

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| objectType | stringType | True | The type of the requested objects to search for. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

Search request to issue against the RevDB Object Index for finding and returning objects.
`query` is required, and represents the query to execute when searching for objects.

`pageSize` and `pageToken` are optional and are used for pagination of large result sets;
see the [Paging](/docs/gotham/api/general/overview/paging) instructions for more information.

If not specified, `pageSize` defaults to a page size of 100 results; 100 is also the maximum allowed page size.

Specifying an invalid page size results in an `InvalidPageSize` [general error](/docs/gotham/api/general/overview/errors#general-errors).

**name:** SearchObjectsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| query | unionType | True |  |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and populate the next request's `pageToken` field with it. |

**example:** {"query":{"type":"and","value":[{"type":"eq","field":"com.palantir.property.name:FIRST_NAME","value":"John"},{"type":"gte","field":"com.palantir.property.age","value":24}]}}

### Response

#### Body

Search Result Payload

**name:** SearchObjectsResponse

**example:** {"data":[{"primaryKey":"ri.gotham.111111-0.object-internal.111111","objectType":"com.palantir.object.person","properties":{"com.palantir.property.name":[{"FIRST_NAME":"John","LAST_NAME":"Smith"}],"com.palantir.property.age":[37]}}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and populate the next request's `pageToken` field with it. |

**example:** {"data":[{"primaryKey":"ri.gotham.111111-0.object-internal.111111","objectType":"com.palantir.object.person","properties":{"com.palantir.property.name":[{"FIRST_NAME":"John","LAST_NAME":"Smith"}],"com.palantir.property.age":[37]}}]}
