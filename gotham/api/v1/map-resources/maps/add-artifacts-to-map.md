---
source_url: "https://www.palantir.com/docs/gotham/api/v1/map-resources/maps/add-artifacts-to-map/"
title: "Add Artifacts To Map"
---
# Add Artifacts To Map

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Add artifacts to a map. Currently only target collection artifacts may be added. If unknown artifacts or artifacts that don't satisfy the security requirements are provided, the entire request will fail. For each request, a new layer is created for each artifact, thus not idempotent. Returns the IDs of the layers created. Path parameters. The RID of the Gaia map that you wish to add artifacts to. Query parameters. Represents a boolean value that restricts an endpoint to preview mode when set to true. Request body. The request body to add artifacts to a map. The GIDs of the artifacts to be added to the map. The name of the layer to be created. Response body. Success response. Examples.
