---
source_url: "https://www.palantir.com/docs/gotham/api/v2/map-rendering-v2-resources/symbols/"
title: "Symbol basics \u2022 API Reference"
---
Loads a PNG format icon with the provided ID, resizing it if requested.
This endpoint has the following features that make it more easily usable from browsers:
  - Respects the If-None-Match etag header, returning 304 if the icon is unchanged.
  - Will use a PALANTIR_TOKEN cookie if no authorization header was provided.
  - Returns Cache-Control and Content-Type headers.
