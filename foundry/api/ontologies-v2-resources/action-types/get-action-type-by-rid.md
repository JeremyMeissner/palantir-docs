---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/action-types/get-action-type-by-rid/"
title: "Get Action Type By Rid \u2022 API Reference"
---
# Get Action Type By Rid

## Endpoint

Gets a specific action type with the given RID.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.getActionTypeByRid

**path:** /api/v2/ontologies/{ontology}/actionTypes/byRid/{actionTypeRid}

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The API name or RID of the Ontology. To find the API name or RID, use the **List Ontologies** endpoint or check the **Ontology Manager**. |
| actionTypeRid | stringType | True | The RID of the action type. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branch | stringType | False | The Foundry branch to load the action type definition from. If not specified, the default branch will be used. Branches are an experimental feature and not all workflows are supported. |

### Response

#### Body

Success response.

**name:** ActionTypeV2

**example:** {"data":{"apiName":"promote-employee","description":"Update an employee's title and compensation","parameters":{"employeeId":{"dataType":{"type":"integer"}},"newTitle":{"dataType":{"type":"string"}},"newCompensation":{"dataType":{"type":"double"}}},"rid":"ri.ontology.main.action-type.7ed72754-7491-428a-bb18-4d7296eb2167"}}

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
| toolDescription | stringType | False | Optional description intended for tool use contexts, such as AI agents. |

**example:** {"data":{"apiName":"promote-employee","description":"Update an employee's title and compensation","parameters":{"employeeId":{"dataType":{"type":"integer"}},"newTitle":{"dataType":{"type":"string"}},"newCompensation":{"dataType":{"type":"double"}}},"rid":"ri.ontology.main.action-type.7ed72754-7491-428a-bb18-4d7296eb2167"}}
