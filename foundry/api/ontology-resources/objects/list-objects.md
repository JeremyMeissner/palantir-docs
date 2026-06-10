---
source_url: "https://www.palantir.com/docs/foundry/api/ontology-resources/objects/list-objects/"
title: "List Objects \u2022 API Reference"
---
# List Objects

## Endpoint

Lists the objects for the given Ontology and object type.

This endpoint supports filtering objects.
See the [Filtering Objects documentation](/docs/foundry/api/ontology-resources/objects/ontology-object-basics#filter-objects) for details.

Note that this endpoint does not guarantee consistency. Changes to the data could result in missing or
repeated objects in the response pages.

For Object Storage V1 backed objects, this endpoint returns a maximum of 10,000 objects. After 10,000 objects have been returned and if more objects
are available, attempting to load another page will result in an `ObjectsExceededLimit` error being returned. There is no limit on Object Storage V2 backed objects.

Each page may be smaller or larger than the requested page size. However, it
is guaranteed that if there are more results available, at least one result will be present
in the response.

Note that null value properties will not be returned.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v1.listObjects

**path:** /api/v1/ontologies/{ontologyRid}/objects/{objectType}

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontologyRid | stringType | True | The unique Resource Identifier (RID) of the Ontology that contains the objects. To look up your Ontology RID, please use the **List ontologies** endpoint or check the **Ontology Manager**. |
| objectType | stringType | True | The API name of the object type. To find the API name, use the **List object types** endpoint or check the **Ontology Manager**. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| pageSize | integerType | False | The desired size of the page to be returned. Defaults to 1,000. See [page sizes](/docs/foundry/api/general/overview/paging/#page-sizes) for details. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| properties | listType | False | The properties of the object type that should be included in the response. Omit this parameter to get all the properties. |
| orderBy | stringType | False | A command representing the list of properties to order by. Properties should be delimited by commas and prefixed by `p` or `properties`. The format expected format is `orderBy=properties.{property}:{sortDirection},properties.{property}:{sortDirection}...`  By default, the ordering for a property is ascending, and this can be explicitly specified by appending  `:asc` (for ascending) or `:desc` (for descending).  Example: use `orderBy=properties.lastName:asc` to order by a single property,  `orderBy=properties.lastName,properties.firstName,properties.age:desc` to order by multiple properties.  You may also use the shorthand `p` instead of `properties` such as `orderBy=p.lastName:asc`. |

### Response

#### Body

Success response.

**name:** ListObjectsResponse

**example:** {"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z","data":[{"rid":"ri.phonograph2-objects.main.object.88a6fccb-f333-46d6-a07e-7725c5f18b61","properties":{"id":50030,"firstName":"John","lastName":"Doe"}},{"rid":"ri.phonograph2-objects.main.object.dcd887d1-c757-4d7a-8619-71e6ec2c25ab","properties":{"id":20090,"firstName":"John","lastName":"Haymore"}}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| data | listType | False | The list of objects in the current page. |
| totalCount | stringType | True | The total number of items across all pages. |

**example:** {"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z","data":[{"rid":"ri.phonograph2-objects.main.object.88a6fccb-f333-46d6-a07e-7725c5f18b61","properties":{"id":50030,"firstName":"John","lastName":"Doe"}},{"rid":"ri.phonograph2-objects.main.object.dcd887d1-c757-4d7a-8619-71e6ec2c25ab","properties":{"id":20090,"firstName":"John","lastName":"Haymore"}}]}
