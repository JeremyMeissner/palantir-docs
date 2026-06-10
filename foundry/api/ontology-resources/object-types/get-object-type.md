---
source_url: "https://www.palantir.com/docs/foundry/api/ontology-resources/object-types/get-object-type/"
title: "Get Object Type \u2022 API Reference"
---
# Get Object Type

## Endpoint

Gets a specific object type with the given API name.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v1.getObjectType

**path:** /api/v1/ontologies/{ontologyRid}/objectTypes/{objectType}

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontologyRid | stringType | True | The unique Resource Identifier (RID) of the Ontology that contains the object type. To look up your Ontology RID, please use the **List ontologies** endpoint or check the **Ontology Manager**. |
| objectType | stringType | True | The API name of the object type. To find the API name, use the **List object types** endpoint or check the **Ontology Manager**. |

### Response

#### Body

Success response.

**name:** ObjectType

**example:** {"apiName":"employee","description":"A full-time or part-time employee of our firm","primaryKey":["employeeId"],"properties":{"employeeId":{"baseType":"Integer"},"fullName":{"baseType":"String"},"office":{"description":"The unique ID of the employee's primary assigned office","baseType":"String"},"startDate":{"description":"The date the employee was hired (most recently, if they were re-hired)","baseType":"Date"}},"rid":"ri.ontology.main.object-type.0381eda6-69bb-4cb7-8ba0-c6158e094a04"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| apiName | stringType | True | The name of the object type in the API in camelCase format. To find the API name for your Object Type, use the `List object types` endpoint or check the **Ontology Manager**. |
| legacyObjectTypeId | stringType | False | The unique ID of an object type. This is a legacy identifier and is not recommended for use in new applications. To find the ID for your Object Type, check the **Ontology Manager**. |
| displayName | stringType | False | The display name of the entity. |
| status | enumType | True | The release status of the entity. |
| description | stringType | False | The description of the object type. |
| visibility | enumType | False | The suggested visibility of the object type. |
| primaryKey | listType | False | The primary key of the object. This is a list of properties that can be used to uniquely identify the object. |
| properties | mapType | False | A map of the properties of the object type. |
| rid | stringType | True | The unique resource identifier of an object type, useful for interacting with other Foundry APIs. |

**example:** {"apiName":"employee","description":"A full-time or part-time employee of our firm","primaryKey":["employeeId"],"properties":{"employeeId":{"baseType":"Integer"},"fullName":{"baseType":"String"},"office":{"description":"The unique ID of the employee's primary assigned office","baseType":"String"},"startDate":{"description":"The date the employee was hired (most recently, if they were re-hired)","baseType":"Date"}},"rid":"ri.ontology.main.object-type.0381eda6-69bb-4cb7-8ba0-c6158e094a04"}
