---
source_url: "https://www.palantir.com/docs/gotham/api/revdb-resources/federated-sources/search-objects-by-federated-source/"
title: "Search objects by federated source \u2022 API Reference"
---
# Search objects by federated source

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::
Search for objects in the specified federated source. The request body is used to filter objects based on the 
specified query. The supported queries depend on what is supported by the federated source. Returns the full 
object.

**operationId:** v1.searchObjectsByFederatedSource

**path:** /api/gotham/v1/federatedSources/{federatedSource}/namespaces/{namespace}/objects/search

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| federatedSource | stringType | True | The name of the federated source to search in. |
| namespace | stringType | True | The namespace of the federated source to search in. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

Search request to issue against a federated federated source for finding and returning objects.
`query` is required, and represents the query to execute when searching for objects. The exact types of queries
allowed depends on the federated source.

`pageSize` and `pageToken` are optional and are used for pagination of large result sets;
see the [Paging](/docs/gotham/api/general/overview/paging) instructions for more information.

If not specified, `pageSize` defaults to a page size of 100 results; 100 is also the maximum allowed page size.

Specifying an invalid page size results in an `InvalidPageSize` [general error](/docs/gotham/api/general/overview/errors#general-errors).

**name:** SearchFederatedSourceObjectsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| query | unionType | True |  |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and populate the next request's `pageToken` field with it. |

**example:** {"query":{"type":"and","value":[{"type":"term","field":"com.palantir.property.name:FIRST_NAME","value":"John"},{"type":"term","field":"com.palantir.property.age","value":24}]}}

### Response

#### Body

A list of the objects that match the search query.

**name:** SearchObjectsResponse

**example:** {"data":[{"primaryKey":"ri.gotham.111111-0.object-internal.111111","objectType":"com.palantir.object.person","properties":{"com.palantir.property.name":[{"FIRST_NAME":"John","LAST_NAME":"Smith"}],"com.palantir.property.age":[37]}}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and populate the next request's `pageToken` field with it. |

**example:** {"data":[{"primaryKey":"ri.gotham.111111-0.object-internal.111111","objectType":"com.palantir.object.person","properties":{"com.palantir.property.name":[{"FIRST_NAME":"John","LAST_NAME":"Smith"}],"com.palantir.property.age":[37]}}]}
