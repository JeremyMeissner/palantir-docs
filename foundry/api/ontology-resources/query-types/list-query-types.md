---
source_url: "https://www.palantir.com/docs/foundry/api/ontology-resources/query-types/list-query-types/"
title: "List Query Types \u2022 API Reference"
---
# List Query Types

## Endpoint

Lists the query types for the given Ontology.

Each page may be smaller than the requested page size. However, it is guaranteed that if there are more
results available, at least one result will be present in the response.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v1.listQueryTypes

**path:** /api/v1/ontologies/{ontologyRid}/queryTypes

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontologyRid | stringType | True | The unique Resource Identifier (RID) of the Ontology that contains the query types. To look up your Ontology RID, please use the **List ontologies** endpoint or check the **Ontology Manager**. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| pageSize | integerType | False | The desired size of the page to be returned. Defaults to 100. See [page sizes](/docs/foundry/api/general/overview/paging/#page-sizes) for details. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

### Response

#### Body

Success response.

**name:** ListQueryTypesResponse

**example:** {"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z","data":[{"apiName":"getEmployeesInCity","displayName":"Get Employees in City","description":"Gets all employees in a given city","parameters":{"city":{"baseType":"String","description":"The city to search for employees in","required":true}},"output":"Array<OntologyObject<Employee>>","rid":"ri.function-registry.main.function.f05481407-1d67-4120-83b4-e3fed5305a29b","version":"1.1.3-rc1"},{"apiName":"getAverageTenureOfEmployees","displayName":"Get Average Tenure","description":"Gets the average tenure of all employees","parameters":{"employees":{"baseType":"String","description":"An object set of the employees to calculate the average tenure of","required":true},"useMedian":{"baseType":"Boolean","description":"An optional flag to use the median instead of the mean, defaults to false","required":false}},"output":"Double","rid":"ri.function-registry.main.function.9549c29d3-e92f-64a1-beeb-af817819a400","version":"2.1.1"}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| data | listType | False |  |

**example:** {"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z","data":[{"apiName":"getEmployeesInCity","displayName":"Get Employees in City","description":"Gets all employees in a given city","parameters":{"city":{"baseType":"String","description":"The city to search for employees in","required":true}},"output":"Array<OntologyObject<Employee>>","rid":"ri.function-registry.main.function.f05481407-1d67-4120-83b4-e3fed5305a29b","version":"1.1.3-rc1"},{"apiName":"getAverageTenureOfEmployees","displayName":"Get Average Tenure","description":"Gets the average tenure of all employees","parameters":{"employees":{"baseType":"String","description":"An object set of the employees to calculate the average tenure of","required":true},"useMedian":{"baseType":"Boolean","description":"An optional flag to use the median instead of the mean, defaults to false","required":false}},"output":"Double","rid":"ri.function-registry.main.function.9549c29d3-e92f-64a1-beeb-af817819a400","version":"2.1.1"}]}
