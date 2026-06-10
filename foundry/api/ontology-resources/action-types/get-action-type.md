---
source_url: "https://www.palantir.com/docs/foundry/api/ontology-resources/action-types/get-action-type/"
title: "Get Action Type \u2022 API Reference"
---
# Get Action Type

## Endpoint

Gets a specific action type with the given API name.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v1.getActionType

**path:** /api/v1/ontologies/{ontologyRid}/actionTypes/{actionTypeApiName}

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontologyRid | stringType | True | The unique Resource Identifier (RID) of the Ontology that contains the action type. |
| actionTypeApiName | stringType | True | The name of the action type in the API. |

### Response

#### Body

Success response.

**name:** ActionType

**example:** {"data":{"apiName":"promote-employee","description":"Update an employee's title and compensation","parameters":{"employeeId":{"baseType":"Integer"},"newTitle":{"baseType":"String"},"newCompensation":{"baseType":"Decimal"}},"rid":"ri.ontology.main.action-type.7ed72754-7491-428a-bb18-4d7296eb2167"}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| apiName | stringType | True | The name of the action type in the API. To find the API name for your Action Type, use the `List action types` endpoint or check the **Ontology Manager**. |
| description | stringType | False |  |
| displayName | stringType | False | The display name of the entity. |
| status | enumType | True | The release status of the entity. |
| parameters | mapType | False |  |
| rid | stringType | True | The unique resource identifier of an action type, useful for interacting with other Foundry APIs. |
| operations | listType | False |  |

**example:** {"data":{"apiName":"promote-employee","description":"Update an employee's title and compensation","parameters":{"employeeId":{"baseType":"Integer"},"newTitle":{"baseType":"String"},"newCompensation":{"baseType":"Decimal"}},"rid":"ri.ontology.main.action-type.7ed72754-7491-428a-bb18-4d7296eb2167"}}
