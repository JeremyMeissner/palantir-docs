---
source_url: "https://www.palantir.com/docs/gotham/api/v1/map-resources/maps/add-objects-to-map/"
parquet_url: "/gotham/api/v1/map-resources/maps/add-objects-to-map/"
title: "Add Objects To Map"
fetched_at: "2026-05-12T19:34:35.728Z"
---
Add Objects To Map. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Add objects to a map. Currently only Foundry-managed object types may be added. If unknown objects or objects that don't satisfy the security requirements are provided, the entire request will fail. This creates a new layer that includes all the provided objects per request, thus not idempotent. Returns the ID of the layer created. Path parameters. The RID of the Gaia map that you wish to add objects to. Query parameters. Represents a boolean value that restricts an endpoint to preview mode when set to true. Request body. The request body to add objects to a map. The name of the layer to be created. Response body. Success response. Examples.
