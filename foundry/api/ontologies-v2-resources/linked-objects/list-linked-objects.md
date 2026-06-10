---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/linked-objects/list-linked-objects/"
title: "List Linked Objects \u2022 API Reference"
---
# List Linked Objects

## Endpoint

Lists the linked objects for a specific object and the given link type.

Note that this endpoint does not guarantee consistency. Changes to the data could result in missing or
repeated objects in the response pages.

For Object Storage V1 backed objects, this endpoint returns a maximum of 10,000 objects. After 10,000 objects have been returned and if more objects
are available, attempting to load another page will result in an `ObjectsExceededLimit` error being returned. There is no limit on Object Storage V2 backed objects.

Each page may be smaller or larger than the requested page size. However, it
is guaranteed that if there are more results available, at least one result will be present
in the response.

Note that null value properties will not be returned.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.listLinkedObjectsV2

**path:** /api/v2/ontologies/{ontology}/objects/{objectType}/{primaryKey}/links/{linkType}

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
| primaryKey | stringType | True | The primary key of the object from which the links originate. To look up the expected primary key for your object type, use the `Get object type` endpoint or the **Ontology Manager**. |
| linkType | stringType | True | The API name of the link that exists between the object and the requested objects. To find the API name for your link type, check the **Ontology Manager**. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| pageSize | integerType | False | The desired size of the page to be returned. Defaults to 1,000. See [page sizes](/docs/foundry/api/general/overview/paging/#page-sizes) for details. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| select | listType | False | The properties of the object type that should be included in the response. Omit this parameter to get all the properties. |
| orderBy | stringType | False | A command representing the list of properties to order by. Properties should be delimited by commas and prefixed by `p` or `properties`. The format expected format is `orderBy=properties.{property}:{sortDirection},properties.{property}:{sortDirection}...`  By default, the ordering for a property is ascending, and this can be explicitly specified by appending  `:asc` (for ascending) or `:desc` (for descending).  Example: use `orderBy=properties.lastName:asc` to order by a single property,  `orderBy=properties.lastName,properties.firstName,properties.age:desc` to order by multiple properties.  You may also use the shorthand `p` instead of `properties` such as `orderBy=p.lastName:asc`. |
| sdkPackageRid | stringType | False | The package rid of the generated SDK. |
| sdkVersion | stringType | False | The version of the generated SDK. |
| excludeRid | booleanType | False | A flag to exclude the retrieval of the `__rid` property.  Setting this to true may improve performance of this endpoint for object types in OSV2. |
| snapshot | booleanType | False | A flag to use snapshot consistency when paging. Setting this to true will give you a consistent view from before you start paging through the results, ensuring you do not get duplicate or missing items. Setting this to false will let new results enter as you page, but you may encounter duplicate or missing items. This defaults to false if not specified, which means you will always get the latest results. |
| branch | stringType | False | The Foundry branch to list linked objects from. If not specified, the default branch will be used. Branches are an experimental feature and not all workflows are supported. |

### Response

#### Body

Success response.

**name:** ListLinkedObjectsResponseV2

**example:** {"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z","data":[{"__rid":"ri.phonograph2-objects.main.object.74f00352-8f13-4764-89ea-28e13e086136","__primaryKey":80060,"__apiName":"Employee","id":80060,"firstName":"Anna","lastName":"Smith"},{"__rid":"ri.phonograph2-objects.main.object.74f00352-8f13-4764-89ea-28e13e086136","__primaryKey":51060,"__apiName":"Employee","id":51060,"firstName":"James","lastName":"Matthews"}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z","data":[{"__rid":"ri.phonograph2-objects.main.object.74f00352-8f13-4764-89ea-28e13e086136","__primaryKey":80060,"__apiName":"Employee","id":80060,"firstName":"Anna","lastName":"Smith"},{"__rid":"ri.phonograph2-objects.main.object.74f00352-8f13-4764-89ea-28e13e086136","__primaryKey":51060,"__apiName":"Employee","id":51060,"firstName":"James","lastName":"Matthews"}]}
