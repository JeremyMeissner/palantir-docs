---
source_url: "https://www.palantir.com/docs/gotham/api/map-resources/maps/load-generic-symbol/"
title: "Load Generic Symbol \u2022 API Reference"
---
# Load Generic Symbol

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Loads a PNG format icon with the provided ID, resizing it if requested.
This endpoint has the following features that make it more easily usable from browsers:
- Respects the If-None-Match etag header, returning 304 if the icon is unchanged.
- Will use a PALANTIR_TOKEN cookie if no authorization header was provided.
- Returns Cache-Control and Content-Type headers.

**operationId:** v1.loadGenericSymbol

**path:** /api/gotham/v1/maprendering/symbols/generic/{id}

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| id | stringType | True | The generic symbol ID returned by the service that uniquely identifies a symbol. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |
| size | integerType | False | Resize the icon so that its reference size matches this value. The actually returned image may be larger or smaller than this value. |

### Response

#### Body

A successful render response.

**name:** body

##### Format
