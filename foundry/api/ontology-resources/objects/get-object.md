---
source_url: "https://www.palantir.com/docs/foundry/api/ontology-resources/objects/get-object/"
title: "Get Object \u2022 API Reference"
---
# Get Object

## Endpoint

Gets a specific object with the given primary key.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v1.getObject

**path:** /api/v1/ontologies/{ontologyRid}/objects/{objectType}/{primaryKey}

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontologyRid | stringType | True | The unique Resource Identifier (RID) of the Ontology that contains the object. To look up your Ontology RID, please use the **List ontologies** endpoint or check the **Ontology Manager**. |
| objectType | stringType | True | The API name of the object type. To find the API name, use the **List object types** endpoint or check the **Ontology Manager**. |
| primaryKey | stringType | True | The primary key of the requested object. To look up the expected primary key for your object type, use the `Get object type` endpoint or the **Ontology Manager**. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| properties | listType | False | The properties of the object type that should be included in the response. Omit this parameter to get all the properties. |

### Response

#### Body

Success response.

**name:** OntologyObject

**example:** {"rid":"ri.phonograph2-objects.main.object.88a6fccb-f333-46d6-a07e-7725c5f18b61","properties":{"id":50030,"firstName":"John","lastName":"Doe"}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| properties | mapType | False | A map of the property values of the object. |
| rid | stringType | True | The unique resource identifier of an object, useful for interacting with other Foundry APIs. |

**example:** {"rid":"ri.phonograph2-objects.main.object.88a6fccb-f333-46d6-a07e-7725c5f18b61","properties":{"id":50030,"firstName":"John","lastName":"Doe"}}
