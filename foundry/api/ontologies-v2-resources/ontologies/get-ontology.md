---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/ontologies/get-ontology/"
title: "Get Ontology \u2022 API Reference"
---
# Get Ontology

## Endpoint

Gets a specific ontology for a given Ontology API name or RID.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.getOntologyV2

**path:** /api/v2/ontologies/{ontology}

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The API name or RID of the Ontology. To find the API name or RID, use the **List Ontologies** endpoint or check the **Ontology Manager**. |

### Response

#### Body

Success response.

**name:** OntologyV2

**example:** {"apiName":"default-ontology","displayName":"Ontology","description":"The default ontology","rid":"ri.ontology.main.ontology.c61d9ab5-2919-4127-a0a1-ac64c0ce6367"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| apiName | stringType | True |  |
| displayName | stringType | True | The display name of the entity. |
| description | stringType | True |  |
| rid | stringType | True | The unique Resource Identifier (RID) of the Ontology. To look up your Ontology RID, please use the `List ontologies` endpoint or check the **Ontology Manager**. |

**example:** {"apiName":"default-ontology","displayName":"Ontology","description":"The default ontology","rid":"ri.ontology.main.ontology.c61d9ab5-2919-4127-a0a1-ac64c0ce6367"}
