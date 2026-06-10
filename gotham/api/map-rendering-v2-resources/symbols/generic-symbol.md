---
source_url: "https://www.palantir.com/docs/gotham/api/map-rendering-v2-resources/symbols/generic-symbol/"
title: "Generic Symbol \u2022 API Reference"
---
# Generic Symbol

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:map-read`.

**operationId:** v2.genericSymbol

**path:** /api/v2/mapRendering/symbols/{symbolId}/generic

### Operation Type

### Scopes

| name |
| --- |
| api:map-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| symbolId | stringType | True | Unique identifier for a symbol that can be used to fetch the symbol as a PNG using loadGenericSymbol endpoint. The ID is opaque and not meant to be parsed in any way. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| size | integerType | True |  |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** body

##### Format

### Error Responses

| name | description |
| --- | --- |
| GenericSymbolPermissionDenied | Could not generic the Symbol. |
