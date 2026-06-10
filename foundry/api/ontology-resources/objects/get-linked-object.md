---
source_url: "https://www.palantir.com/docs/foundry/api/ontology-resources/objects/get-linked-object/"
title: "Get Linked Object \u2022 API Reference"
---
# Get Linked Object

## Endpoint

Get a specific linked object that originates from another object. If there is no link between the two objects,
LinkedObjectNotFound is thrown.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v1.getLinkedObject

**path:** /api/v1/ontologies/{ontologyRid}/objects/{objectType}/{primaryKey}/links/{linkType}/{linkedObjectPrimaryKey}

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontologyRid | stringType | True | The unique Resource Identifier (RID) of the Ontology that contains the object. To look up your Ontology RID, please use the **List ontologies** endpoint or check the **Ontology Manager**. |
| objectType | stringType | True | The API name of the object from which the links originate. To find the API name, use the **List object types** endpoint or check the **Ontology Manager**. |
| primaryKey | stringType | True | The primary key of the object from which the link originates. To look up the expected primary key for your object type, use the `Get object type` endpoint or the **Ontology Manager**. |
| linkType | stringType | True | The API name of the link that exists between the object and the requested objects. To find the API name for your link type, check the **Ontology Manager**. |
| linkedObjectPrimaryKey | stringType | True | The primary key of the requested linked object. To look up the expected primary key for your object type, use the `Get object type` endpoint (passing the linked object type) or the **Ontology Manager**. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| properties | listType | False | The properties of the object type that should be included in the response. Omit this parameter to get all the properties. |

### Response

#### Body

Success response.

**name:** OntologyObject

**example:** {"rid":"ri.phonograph2-objects.main.object.74f00352-8f13-4764-89ea-28e13e086136","properties":{"id":80060,"firstName":"Anna","lastName":"Smith"}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| properties | mapType | False | A map of the property values of the object. |
| rid | stringType | True | The unique resource identifier of an object, useful for interacting with other Foundry APIs. |

**example:** {"rid":"ri.phonograph2-objects.main.object.74f00352-8f13-4764-89ea-28e13e086136","properties":{"id":80060,"firstName":"Anna","lastName":"Smith"}}
