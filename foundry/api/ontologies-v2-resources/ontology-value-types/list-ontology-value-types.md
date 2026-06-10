---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/ontology-value-types/list-ontology-value-types/"
title: "List Ontology Value Types \u2022 API Reference"
---
# List Ontology Value Types

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Lists the latest versions of the value types for the given Ontology.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.listOntologyValueTypes

**path:** /api/v2/ontologies/{ontology}/valueTypes

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The API name or RID of the Ontology. To find the API name or RID, use the **List Ontologies** endpoint or check the **Ontology Manager**. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |

### Response

#### Body

Success response.

**name:** ListOntologyValueTypesResponse

**example:** {"data":[{"apiName":"validNorthAmericanCountries","description":"Options for valid countries in North America","displayName":"Valid North American Countries","status":"ACTIVE","fieldType":"string","rid":"ri.type-registry.main.value-type.f5ee06ef-6dfd-4d91-a01e-91bd457c719d","constraints":[{"type":"enum","enum":{"options":["USA","Mexico","Canada"]}}]},{"apiName":"countyCode","description":"A three letter code for a US County.","displayName":"County Code","status":"ACTIVE","fieldType":"string","rid":"ri.type-registry.main.value-type.f5ee06ef-6dfd-4d91-a01e-91bd457c8232","constraints":[{"type":"length","length":{"minimumLength":3,"maximumLength":3}}]}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |

**example:** {"data":[{"apiName":"validNorthAmericanCountries","description":"Options for valid countries in North America","displayName":"Valid North American Countries","status":"ACTIVE","fieldType":"string","rid":"ri.type-registry.main.value-type.f5ee06ef-6dfd-4d91-a01e-91bd457c719d","constraints":[{"type":"enum","enum":{"options":["USA","Mexico","Canada"]}}]},{"apiName":"countyCode","description":"A three letter code for a US County.","displayName":"County Code","status":"ACTIVE","fieldType":"string","rid":"ri.type-registry.main.value-type.f5ee06ef-6dfd-4d91-a01e-91bd457c8232","constraints":[{"type":"length","length":{"minimumLength":3,"maximumLength":3}}]}]}
