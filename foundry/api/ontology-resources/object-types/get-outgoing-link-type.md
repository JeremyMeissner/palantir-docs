---
source_url: "https://www.palantir.com/docs/foundry/api/ontology-resources/object-types/get-outgoing-link-type/"
title: "Get Outgoing Link Type \u2022 API Reference"
---
# Get Outgoing Link Type

## Endpoint

Get an outgoing link for an object type.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v1.getOutgoingLinkType

**path:** /api/v1/ontologies/{ontologyRid}/objectTypes/{objectType}/outgoingLinkTypes/{linkType}

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontologyRid | stringType | True | The unique Resource Identifier (RID) of the Ontology that contains the object type. To look up your Ontology RID, please use the **List ontologies** endpoint or check the **Ontology Manager** application. |
| objectType | stringType | True | The API name of the object type. To find the API name, use the **List object types** endpoint or check the **Ontology Manager** application. |
| linkType | stringType | True | The API name of the outgoing link. To find the API name for your link type, check the **Ontology Manager**. |

### Response

#### Body

Success response.

**name:** LinkTypeSide

**example:** {"apiName":"directReport","objectTypeApiName":"Employee","cardinality":"MANY"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| apiName | stringType | True | The name of the link type in the API. To find the API name for your Link Type, check the **Ontology Manager** application. |
| displayName | stringType | True | The display name of the entity. |
| status | enumType | True | The release status of the entity. |
| objectTypeApiName | stringType | True | The name of the object type in the API in camelCase format. To find the API name for your Object Type, use the `List object types` endpoint or check the **Ontology Manager**. |
| cardinality | enumType | True |  |
| foreignKeyPropertyApiName | stringType | False | The name of the property in the API. To find the API name for your property, use the `Get object type` endpoint or check the **Ontology Manager**. |

**example:** {"apiName":"directReport","objectTypeApiName":"Employee","cardinality":"MANY"}
