---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/object-types/get-object-type/"
title: "Get Object Type \u2022 API Reference"
---
# Get Object Type

## Endpoint

Gets a specific object type with the given API name.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.getObjectTypeV2

**path:** /api/v2/ontologies/{ontology}/objectTypes/{objectType}

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

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branch | stringType | False | The Foundry branch to load the object type definition from. If not specified, the default branch will be used. Branches are an experimental feature and not all workflows are supported. |

### Response

#### Body

Success response.

**name:** ObjectTypeV2

**example:** {"apiName":"employee","description":"A full-time or part-time employee of our firm","displayName":"Employee","status":"ACTIVE","primaryKey":"employeeId","properties":{"employeeId":{"dataType":{"type":"integer"},"rid":"ri.ontology.main.property.571d3d4d-150a-4dd4-b1a7-d16c1ed7d996"},"fullName":{"dataType":{"type":"string"},"rid":"ri.ontology.main.property.5721baa7-26d5-4ca8-b092-d47dcc724ab1"},"office":{"description":"The unique ID of the employee's primary assigned office","dataType":{"type":"string"},"rid":"ri.ontology.main.property.554fa8c4-3b6e-4d3f-adef-acc9f0f54633"},"startDate":{"description":"The date the employee was hired (most recently, if they were re-hired)","dataType":{"type":"date"},"rid":"ri.ontology.main.property.3b081417-fe68-4010-ade8-68b298116ed4"}},"rid":"ri.ontology.main.object-type.0381eda6-69bb-4cb7-8ba0-c6158e094a04"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| apiName | stringType | True | The name of the object type in the API in camelCase format. To find the API name for your Object Type, use the `List object types` endpoint or check the **Ontology Manager**. |
| displayName | stringType | True | The display name of the entity. |
| status | enumType | True | The release status of the entity. |
| description | stringType | False | The description of the object type. |
| pluralDisplayName | stringType | True | The plural display name of the object type. |
| icon | unionType | True | A union currently only consisting of the BlueprintIcon (more icon types may be added in the future). |
| primaryKey | stringType | True | The name of the property in the API. To find the API name for your property, use the `Get object type` endpoint or check the **Ontology Manager**. |
| properties | mapType | False | A map of the properties of the object type. |
| rid | stringType | True | The unique resource identifier of an object type, useful for interacting with other Foundry APIs. |
| titleProperty | stringType | True | The name of the property in the API. To find the API name for your property, use the `Get object type` endpoint or check the **Ontology Manager**. |
| visibility | enumType | False | The suggested visibility of the object type. |

**example:** {"apiName":"employee","description":"A full-time or part-time employee of our firm","displayName":"Employee","status":"ACTIVE","primaryKey":"employeeId","properties":{"employeeId":{"dataType":{"type":"integer"},"rid":"ri.ontology.main.property.571d3d4d-150a-4dd4-b1a7-d16c1ed7d996"},"fullName":{"dataType":{"type":"string"},"rid":"ri.ontology.main.property.5721baa7-26d5-4ca8-b092-d47dcc724ab1"},"office":{"description":"The unique ID of the employee's primary assigned office","dataType":{"type":"string"},"rid":"ri.ontology.main.property.554fa8c4-3b6e-4d3f-adef-acc9f0f54633"},"startDate":{"description":"The date the employee was hired (most recently, if they were re-hired)","dataType":{"type":"date"},"rid":"ri.ontology.main.property.3b081417-fe68-4010-ade8-68b298116ed4"}},"rid":"ri.ontology.main.object-type.0381eda6-69bb-4cb7-8ba0-c6158e094a04"}
