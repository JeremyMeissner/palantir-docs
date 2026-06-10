---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/ontology-object-sets/load-object-set-multiple-object-types/"
title: "Load Object Set Multiple Object Types \u2022 API Reference"
---
# Load Object Set Multiple Object Types

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Load the ontology objects present in the `ObjectSet` from the provided object set definition. The resulting 
objects may be scoped to an object type, in which all the selected properties on the object type are returned, or scoped 
to an interface, in which only the object type properties that implement the properties of any interfaces in its 
scope are returned. For objects that are scoped to an interface in the result, a mapping from interface to 
object implementation is returned in order to interpret the objects as the interfaces that they implement.

For Object Storage V1 backed objects, this endpoint returns a maximum of 10,000 objects. After 10,000 objects have been returned and if more objects
are available, attempting to load another page will result in an `ObjectsExceededLimit` error being returned. There is no limit on Object Storage V2 backed objects.

Note that null value properties will not be returned. In addition, property metadata (rid, apiName, and primaryKey)
will be prefixed with '$' instead of '__' as is the case in `loadObjects`.

Vector properties will not be returned unless included in the `select` parameter.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.loadObjectSetV2MultipleObjectTypes

**path:** /api/v2/ontologies/{ontology}/objectSets/loadObjectsMultipleObjectTypes

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
| branch | stringType | False | The Foundry branch to load the object set for multiple object types. If not specified, the default branch is used. Branches are an experimental feature and not all workflows are supported. |
| transactionId | stringType | False | The ID of an Ontology transaction to read from. Transactions are an experimental feature and all workflows may not be supported. |
| scenarioRid | stringType | False | The resource identifier of an ontology scenario to load the object set from. |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |
| executeInMemoryOnly | booleanType | False | If true, the request fails with an error when it cannot be computed in-memory. Use this to opt into fast failure on requests that would otherwise require heavier computation.  Defaults to false. |

### Request

#### Body

Represents the API POST body when loading an `ObjectSet`. Used on the `/loadObjectsMultipleObjectTypes` endpoint only.

**name:** LoadObjectSetV2MultipleObjectTypesRequest

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
| loadPropertySecurities | booleanType | False | A flag to load the securities for all properties. Setting this flag to true will return a list of securities in the `propertySecurities` field of the response. Returned objects will return all properties as Secured Property Values, which provide the property data as well an index into the `propertySecurities` list. This feature is experimental and not yet generally available. |
| snapshot | booleanType | False | A flag to use snapshot consistency when paging. Setting this to true will give you a consistent view from before you start paging through the results, ensuring you do not get duplicate or missing items. Setting this to false will let new results enter as you page, but you may encounter duplicate or missing items. This defaults to false if not specified, which means you will always get the latest results. |
| includeComputeUsage | booleanType | False | Indicates whether the response should include compute usage details for the request. This feature is currently only available for OSDK applications. Note: Enabling this flag may slow down query performance and is not recommended for use in production. |

**example:** {"objectSet":{"type":"base","objectType":"Employee"},"pageSize":10000,"pageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Response

#### Body

Success response.

**name:** LoadObjectSetV2MultipleObjectTypesResponse

**example:** {"data":[{"$rid":"ri.phonograph2-objects.main.object.5b5dbc28-7f05-4e83-a33a-1e5b851","$primaryKey":50030,"$apiName":"Employee","employeeId":50030,"employeeName":"John"},{"$rid":"ri.phonograph2-objects.main.object.88a6fccb-f333-46d6-a07e-7725c5f18b61","$primaryKey":20090,"$apiName":"Employee","employeeId":20090,"employeeName":"John"},{"$rid":"ri.phonograph2-objects.main.object.88a6fccb-f333-46d6-a07e-7725c5f18b71","$primaryKey":23,"$apiName":"Athlete","jerseyNumber":23,"firstName":"Michael"}],"totalCount":"3,","interfaceToObjectTypeMappings":{"Person":{"Employee":{"first":"employeeName","identifier":"employeeId"},"Athlete":{"first":"firstName","identifier":"jerseyNumber"}}}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False | The list of objects in the current page. |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| totalCount | stringType | True | The total number of items across all pages. |
| interfaceToObjectTypeMappings | mapType | False |  |
| interfaceToObjectTypeMappingsV2 | mapType | False |  |
| computeUsage | numberType | False | A measurement of compute usage expressed in [compute-seconds](/docs/foundry/resource-management/usage-types#compute-second). For more information, please refer to the [Usage types](/docs/foundry/resource-management/usage-types) documentation. |
| propertySecurities | listType | False |  |

**example:** {"data":[{"$rid":"ri.phonograph2-objects.main.object.5b5dbc28-7f05-4e83-a33a-1e5b851","$primaryKey":50030,"$apiName":"Employee","employeeId":50030,"employeeName":"John"},{"$rid":"ri.phonograph2-objects.main.object.88a6fccb-f333-46d6-a07e-7725c5f18b61","$primaryKey":20090,"$apiName":"Employee","employeeId":20090,"employeeName":"John"},{"$rid":"ri.phonograph2-objects.main.object.88a6fccb-f333-46d6-a07e-7725c5f18b71","$primaryKey":23,"$apiName":"Athlete","jerseyNumber":23,"firstName":"Michael"}],"totalCount":"3,","interfaceToObjectTypeMappings":{"Person":{"Employee":{"first":"employeeName","identifier":"employeeId"},"Athlete":{"first":"firstName","identifier":"jerseyNumber"}}}}
