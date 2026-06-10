---
source_url: "https://www.palantir.com/docs/gotham/api/v1/map-resources/maps/load-generic-symbol/"
parquet_url: "/gotham/api/v1/map-resources/maps/load-generic-symbol/"
title: "Load Generic Symbol"
fetched_at: "2026-05-12T19:34:35.736Z"
---
Load Generic Symbol. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Loads a PNG format icon with the provided ID, resizing it if requested. This endpoint has the following features that make it more easily usable from browsers: Respects the If-None-Match etag header, returning 304 if the icon is unchanged. Will use a PALANTIR_TOKEN cookie if no authorization header was provided. Returns Cache-Control and Content-Type headers. Path parameters. The generic symbol ID returned by the service that uniquely identifies a symbol. Query parameters. Represents a boolean value that restricts an endpoint to preview mode when set to true. Resize the icon so that its reference size matches this value. The actually returned image may be larger or smaller than this value. Response body. A successful render response. Examples.
