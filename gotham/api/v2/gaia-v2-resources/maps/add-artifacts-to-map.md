---
source_url: "https://www.palantir.com/docs/gotham/api/v2/gaia-v2-resources/maps/add-artifacts-to-map/"
parquet_url: "/gotham/api/v2/gaia-v2-resources/maps/add-artifacts-to-map/"
title: "Add Artifacts To Map"
fetched_at: "2026-05-12T19:34:35.762Z"
---
Add Artifacts To Map. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Add artifacts to a map. Currently only Foundry-managed object types may be added. If unknown objects or objects that don't satisfy the security requirements are provided, the entire request will fail. This creates a new layer that includes all the provided objects per request, thus not idempotent. Returns the IDs of the layers created. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:map-write. Path parameters. The RID of a Gaia map. Query parameters. Enables the use of preview functionality. Request body. The GIDs of artifacts to be added to the map. The name of the layer to be created. Response body. The response body to add artifacts to a map, containing the IDs of the created layers. Examples. Error responses.
