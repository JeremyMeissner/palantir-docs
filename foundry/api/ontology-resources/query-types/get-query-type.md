---
source_url: "https://www.palantir.com/docs/foundry/api/ontology-resources/query-types/get-query-type/"
title: "Get Query Type \u2022 API Reference"
---
# Get Query Type

## Endpoint

Gets a specific query type with the given API name.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v1.getQueryType

**path:** /api/v1/ontologies/{ontologyRid}/queryTypes/{queryApiName}

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontologyRid | stringType | True | The unique Resource Identifier (RID) of the Ontology that contains the query type. To look up your Ontology RID, please use the **List ontologies** endpoint or check the **Ontology Manager**. |
| queryApiName | stringType | True | The API name of the query type. To find the API name, use the **List query types** endpoint or check the **Ontology Manager**. |

### Response

#### Body

Success response.

**name:** QueryType

**example:** {"apiName":"getEmployeesInCity","displayName":"Get Employees in City","description":"Gets all employees in a given city","parameters":{"city":{"baseType":"String","description":"The city to search for employees in","required":true}},"output":"Array<OntologyObject<Employee>>","rid":"ri.function-registry.main.function.f05481407-1d67-4120-83b4-e3fed5305a29b","version":"1.1.3-rc1"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| apiName | stringType | True | The name of the Query in the API. |
| description | stringType | False |  |
| displayName | stringType | False | The display name of the entity. |
| parameters | mapType | False |  |
| output | unionType | False | A union of all the primitive types used by Palantir's Ontology-based products. |
| rid | stringType | True | The unique resource identifier of a Function, useful for interacting with other Foundry APIs. |
| version | stringType | True | The version of the given Function, written `<major>.<minor>.<patch>-<tag>`, where `-<tag>` is optional. Examples: `1.2.3`, `1.2.3-rc1`. |

**example:** {"apiName":"getEmployeesInCity","displayName":"Get Employees in City","description":"Gets all employees in a given city","parameters":{"city":{"baseType":"String","description":"The city to search for employees in","required":true}},"output":"Array<OntologyObject<Employee>>","rid":"ri.function-registry.main.function.f05481407-1d67-4120-83b4-e3fed5305a29b","version":"1.1.3-rc1"}
