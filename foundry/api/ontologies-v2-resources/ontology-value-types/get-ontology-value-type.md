---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/ontology-value-types/get-ontology-value-type/"
title: "Get Ontology Value Type \u2022 API Reference"
---
# Get Ontology Value Type

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Gets a specific value type with the given API name.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.getOntologyValueType

**path:** /api/v2/ontologies/{ontology}/valueTypes/{valueType}

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The API name or RID of the Ontology. To find the API name or RID, use the **List Ontologies** endpoint or check the **Ontology Manager**. |
| valueType | stringType | True | The API name of the value type. To find the API name, use the **List value types** endpoint or check the **Ontology Manager**. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |

### Response

#### Body

Success response.

**name:** OntologyValueType

**example:** {"apiName":"countryInitials","description":"A three letter code for a top-level administrative region","displayName":"Country Initials","status":"ACTIVE","fieldType":"string","rid":"ri.type-registry.main.value-type.f5ee06ef-6dfd-4d91-a01e-91bd457c719d","constraints":[{"type":"length","length":{"minimumLength":3,"maximumLength":3}}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| apiName | stringType | True | The name of the value type in the API in camelCase format. |
| displayName | stringType | True | The display name of the entity. |
| description | stringType | False |  |
| rid | stringType | True |  |
| status | enumType | False |  |
| fieldType | unionType | True |  |
| version | stringType | True |  |
| constraints | listType | False |  |

**example:** {"apiName":"countryInitials","description":"A three letter code for a top-level administrative region","displayName":"Country Initials","status":"ACTIVE","fieldType":"string","rid":"ri.type-registry.main.value-type.f5ee06ef-6dfd-4d91-a01e-91bd457c719d","constraints":[{"type":"length","length":{"minimumLength":3,"maximumLength":3}}]}
