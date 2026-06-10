---
source_url: "https://www.palantir.com/docs/gotham/api/gaia-v2-resources/maps/render-symbol-map/"
title: "Render Symbol Map \u2022 API Reference"
---
# Render Symbol Map

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Fetches the PNG for the given symbol identifier

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:map-read`.

**operationId:** v2.renderSymbolMap

**path:** /api/v2/gaia/maps/renderSymbol

### Operation Type

### Scopes

| name |
| --- |
| api:map-read |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** RenderSymbolMapRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| value | unionType | True |  |

**example:** {"value":{"type":"MilsymSymbol","sidc":"SHG-USTI-------"}}

### Response

#### Body

**name:** body

##### Format

### Error Responses

| name | description |
| --- | --- |
| ErrorExportingSymbol | Failed to export symbol. |
| UnknownSymbolType | Unknown symbol type not supported, must be either IconSymbol or MilsymSymbol. |
| InvalidUrlSymbol | Url Symbol not supported, must be either IconSymbol or MilsymSymbol. |
| RenderSymbolMapPermissionDenied | Could not renderSymbol the Map. |
