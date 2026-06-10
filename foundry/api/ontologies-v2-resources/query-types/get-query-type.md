---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/query-types/get-query-type/"
title: "Get Query Type \u2022 API Reference"
---
# Get Query Type

## Endpoint

Gets a specific query type with the given API name.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.getQueryTypeV2

**path:** /api/v2/ontologies/{ontology}/queryTypes/{queryApiName}

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The API name or RID of the Ontology. To find the API name or RID, use the **List Ontologies** endpoint or check the **Ontology Manager**. |
| queryApiName | stringType | True | The API name of the query type. To find the API name, use the **List query types** endpoint or check the **Ontology Manager**. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| version | stringType | False | The version of the Query to get. |
| sdkPackageRid | stringType | False | The package rid of the generated SDK. |
| sdkVersion | stringType | False | The version of the generated SDK. |

### Response

#### Body

Success response.

**name:** QueryTypeV2

**example:** {"apiName":"getEmployeesInCity","displayName":"Get Employees in City","description":"Gets all employees in a given city","parameters":{"city":{"dataType":{"type":"string"},"description":"The city to search for employees in","required":true}},"output":{"dataType":{"type":"array","subType":{"type":"object","objectApiName":"Employee"}},"required":true},"rid":"ri.function-registry.main.function.f05481407-1d67-4120-83b4-e3fed5305a29b","version":"1.1.3-rc1"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| apiName | stringType | True | The name of the Query in the API. |
| description | stringType | False |  |
| displayName | stringType | False | The display name of the entity. |
| parameters | mapType | False |  |
| output | unionType | True | A union of all the types supported by Ontology Query parameters or outputs. |
| rid | stringType | True | The unique resource identifier of a Function, useful for interacting with other Foundry APIs. |
| version | stringType | True | The version of the given Function, written `<major>.<minor>.<patch>-<tag>`, where `-<tag>` is optional. Examples: `1.2.3`, `1.2.3-rc1`. |
| typeReferences | mapType | False |  |

**example:** {"apiName":"getEmployeesInCity","displayName":"Get Employees in City","description":"Gets all employees in a given city","parameters":{"city":{"dataType":{"type":"string"},"description":"The city to search for employees in","required":true}},"output":{"dataType":{"type":"array","subType":{"type":"object","objectApiName":"Employee"}},"required":true},"rid":"ri.function-registry.main.function.f05481407-1d67-4120-83b4-e3fed5305a29b","version":"1.1.3-rc1"}
