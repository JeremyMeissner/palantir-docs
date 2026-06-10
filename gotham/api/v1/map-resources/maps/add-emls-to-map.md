---
source_url: "https://www.palantir.com/docs/gotham/api/v1/map-resources/maps/add-emls-to-map/"
title: "Add Enterprise Map Layers To Map"
---
# Add Enterprise Map Layers To Map

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Add enterprise map layers to a map. If unknown enterprise map layers or enterprise map layers that don't satisfy the security requirements are provided, the entire request will fail. For each request, a new layer is created for each enterprise map layer provided, thus not idempotent. Returns the IDs of the layers created. Path parameters. The RID of the Gaia map that you wish to add objects to. Query parameters. Represents a boolean value that restricts an endpoint to preview mode when set to true. Request body. The request body to add enterprise map layers to a map. The IDs of the enterprise map layers to be added to the map. Response body. Success response. Examples.
