---
source_url: "https://www.palantir.com/docs/gotham/api/map-resources/maps/render-symbol/"
title: "Rendering Symbology \u2022 API Reference"
---
# Rendering Symbology

## Endpoint

Fetches the PNG for the given symbol identifier

**operationId:** v1.renderSymbol

**path:** /api/gotham/v1/maps/rendering/symbol

### Operation Type

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

**name:** GaiaSymbol

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| MilsymSymbol | objectType | False |  |
| IconSymbol | objectType | False |  |

**example:** {"type":"MilsymSymbol","sidc":"SHG-USTI-------"}

### Response

#### Body

A successful render response.

**name:** body

##### Format
