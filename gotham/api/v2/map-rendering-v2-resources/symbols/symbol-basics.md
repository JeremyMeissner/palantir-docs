---
source_url: "https://www.palantir.com/docs/gotham/api/v2/map-rendering-v2-resources/symbols/symbol-basics/"
parquet_url: "/gotham/api/v2/map-rendering-v2-resources/symbols/symbol-basics/"
title: "Symbol basics"
fetched_at: "2026-05-12T19:34:35.756Z"
---
Symbol basics. Loads a PNG format icon with the provided ID, resizing it if requested. This endpoint has the following features that make it more easily usable from browsers: Respects the If-None-Match etag header, returning 304 if the icon is unchanged. Will use a PALANTIR_TOKEN cookie if no authorization header was provided. Returns Cache-Control and Content-Type headers.
