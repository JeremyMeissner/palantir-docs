---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/ontology-object-sets/load-object-set-objects-or-interfaces/"
title: "Load Object Set Objects Or Interfaces \u2022 API Reference"
---
# Load Object Set Objects Or Interfaces

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Load the ontology objects present in the `ObjectSet` from the provided object set definition. If the requested 
object set contains interfaces and the object can be viewed as an interface, it will contain the properties 
defined by the interface. If not, it will contain the properties defined by its object type. This allows directly
loading all objects of an interface where all objects are viewed as the interface, for example.

Note that the result object set cannot contain a mix of objects with "interface" properties and "object type"
properties. Attempting to load an object set like this will result in an error.

For Object Storage V1 backed objects, this endpoint returns a maximum of 10,000 objects. After 10,000 objects have been returned and if more objects
are available, attempting to load another page will result in an `ObjectsExceededLimit` error being returned. There is no limit on Object Storage V2 backed objects.

Note that null value properties will not be returned. In addition, property metadata (rid, apiName, and primaryKey)
will be prefixed with '$' instead of '__' as is the case in `/loadObjects`.

Vector properties will not be returned unless included in the `select` parameter.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.loadObjectSetV2ObjectsOrInterfaces

**path:** /api/v2/ontologies/{ontology}/objectSets/loadObjectsOrInterfaces

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
| branch | stringType | False | The Foundry branch to load the objects or interfaces from. If not specified, the default branch is used. Branches are an experimental feature and not all workflows are supported. |
| transactionId | stringType | False | The ID of an Ontology transaction to read from. Transactions are an experimental feature and all workflows may not be supported. |
| scenarioRid | stringType | False | The resource identifier of an ontology scenario to load the objects or interfaces from. |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |
| executeInMemoryOnly | booleanType | False | If true, the request fails with an error when it cannot be computed in-memory. Use this to opt into fast failure on requests that would otherwise require heavier computation.  Defaults to false. |

### Request

#### Body

Represents the API POST body when loading an `ObjectSet`. Used on the `/loadObjectsOrInterfaces` endpoint only.

**name:** LoadObjectSetV2ObjectsOrInterfacesRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| objectSet | unionType | True | Represents the definition of an `ObjectSet` in the `Ontology`. |
| orderBy | objectType | False | Specifies the ordering of search results by a field and an ordering direction or by relevance if scores are required in a nearestNeighbors query. By default `orderType` is set to `fields`. |
| select | listType | False |  |
| selectV2 | listType | False | The identifiers of the properties to include in the response. Only selectV2 or select should be populated, but not both. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| pageSize | integerType | False | The page size to use for the endpoint. |
| excludeRid | booleanType | False | A flag to exclude the retrieval of the `$rid` property. Setting this to true may improve performance of this endpoint for object types in OSV2. |
| snapshot | booleanType | False | A flag to use snapshot consistency when paging. Setting this to true will give you a consistent view from before you start paging through the results, ensuring you do not get duplicate or missing items. Setting this to false will let new results enter as you page, but you may encounter duplicate or missing items. This defaults to false if not specified, which means you will always get the latest results. |

**example:** {"objectSet":{"type":"interfaceBase","interfaceType":"Person"},"pageSize":10000,"pageToken":"v1.VGhlcmUgaXMgc28gbXVjaCBsZWZ0IHRvIGJ1aWxkIC0gcGFsYW50aXIuY29tL2NhcmVlcnMv"}

### Response

#### Body

Success response.

**name:** LoadObjectSetV2ObjectsOrInterfacesResponse

**example:** {"data":[{"$rid":"ri.phonograph2-objects.main.object.5b5dbc28-7f05-4e83-a33a-1e5b851","$primaryKey":50030,"$objectTypeApiName":"Employee","$interfaceTypeApiName":"Person","personId":50030,"firstName":"John"},{"$rid":"ri.phonograph2-objects.main.object.88a6fccb-f333-46d6-a07e-7725c5f18b61","$primaryKey":20090,"$objectTypeApiName":"Employee","$interfaceTypeApiName":"Person","personID":20090,"firstName":"John"},{"$rid":"ri.phonograph2-objects.main.object.88a6fccb-f333-46d6-a07e-7725c5f18b71","$primaryKey":23,"$objectTypeApiName":"Athlete","$interfaceTypeApiName":"Person","personId":23,"firstName":"Michael"}],"totalCount":3}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False | The list of objects in the current page. |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| totalCount | stringType | True | The total number of items across all pages. |
| transactionId | stringType | False | The ID identifying a transaction. |

**example:** {"data":[{"$rid":"ri.phonograph2-objects.main.object.5b5dbc28-7f05-4e83-a33a-1e5b851","$primaryKey":50030,"$objectTypeApiName":"Employee","$interfaceTypeApiName":"Person","personId":50030,"firstName":"John"},{"$rid":"ri.phonograph2-objects.main.object.88a6fccb-f333-46d6-a07e-7725c5f18b61","$primaryKey":20090,"$objectTypeApiName":"Employee","$interfaceTypeApiName":"Person","personID":20090,"firstName":"John"},{"$rid":"ri.phonograph2-objects.main.object.88a6fccb-f333-46d6-a07e-7725c5f18b71","$primaryKey":23,"$objectTypeApiName":"Athlete","$interfaceTypeApiName":"Person","personId":23,"firstName":"Michael"}],"totalCount":3}
