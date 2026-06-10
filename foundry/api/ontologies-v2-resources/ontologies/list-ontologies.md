---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/ontologies/list-ontologies/"
title: "List Ontologies \u2022 API Reference"
---
# List Ontologies

## Endpoint

Lists the Ontologies visible to the current user.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.listOntologiesV2

**path:** /api/v2/ontologies

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Response

#### Body

Success response.

**name:** ListOntologiesV2Response

**example:** {"data":[{"apiName":"default-ontology","displayName":"Ontology","description":"The default ontology","rid":"ri.ontology.main.ontology.c61d9ab5-2919-4127-a0a1-ac64c0ce6367"},{"apiName":"shared-ontology","displayName":"Shared ontology","description":"The ontology shared with our suppliers","rid":"ri.ontology.main.ontology.c61d9ab5-2919-4127-a0a1-ac64c0ce6367"}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False | The list of Ontologies the user has access to. |

**example:** {"data":[{"apiName":"default-ontology","displayName":"Ontology","description":"The default ontology","rid":"ri.ontology.main.ontology.c61d9ab5-2919-4127-a0a1-ac64c0ce6367"},{"apiName":"shared-ontology","displayName":"Shared ontology","description":"The ontology shared with our suppliers","rid":"ri.ontology.main.ontology.c61d9ab5-2919-4127-a0a1-ac64c0ce6367"}]}
