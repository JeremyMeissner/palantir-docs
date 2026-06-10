---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/object-types/get-outgoing-link-type/"
title: "Get Outgoing Link Type \u2022 API Reference"
---
# Get Outgoing Link Type

## Endpoint

Get an outgoing link for an object type.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.getOutgoingLinkTypeV2

**path:** /api/v2/ontologies/{ontology}/objectTypes/{objectType}/outgoingLinkTypes/{linkType}

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The API name or RID of the Ontology. To find the API name or RID, use the **List Ontologies** endpoint or check the **Ontology Manager**. |
| objectType | stringType | True | The API name of the object type. To find the API name, use the **List object types** endpoint or check the **Ontology Manager** application. |
| linkType | stringType | True | The API name of the outgoing link. To find the API name for your link type, check the **Ontology Manager**. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branch | stringType | False | The Foundry branch to get the outgoing link types for an object type from. If not specified, the default branch will be used. Branches are an experimental feature and not all workflows are supported. |

### Response

#### Body

Success response.

**name:** LinkTypeSideV2

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
| linkTypeRid | stringType | True |  |

**example:** {"apiName":"directReport","objectTypeApiName":"Employee","cardinality":"MANY"}
