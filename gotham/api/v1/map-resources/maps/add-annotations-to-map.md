---
source_url: "https://www.palantir.com/docs/gotham/api/v1/map-resources/maps/add-annotations-to-map/"
parquet_url: "/gotham/api/v1/map-resources/maps/add-annotations-to-map/"
title: "Add Annotations To Map"
fetched_at: "2026-05-12T19:34:35.736Z"
---
Add Annotations To Map. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Add annotations to a map. Currently only Line, Polygon, Rectangle, Point, and tactical graphic annotations may be added. If any provided parameters are unknown, invalid, or do not satisfy the security requirements, the entire request will fail. For each request, a new element is created for each annotation, as well as a new layer if no parent layer is specified; thus not idempotent. Returns the ID of the layer created. Path parameters. The RID of the Gaia map that you wish to add annotations to. Query parameters. Represents a boolean value that restricts an endpoint to preview mode when set to true. Request body. The request body to add annotations to a map. The ID of a layer in a Gaia map. If provided AND no existing parentLayerId is provided, the new layer created will be set with the provided label. The annotations to be added to the map. Response body. Success response. The ID of a layer in a Gaia map. The IDs of the created annotations. Examples.
