---
source_url: "https://www.palantir.com/docs/gotham/api/v2/gaia-v2-resources/maps/load-layers-map/"
parquet_url: "/gotham/api/v2/gaia-v2-resources/maps/load-layers-map/"
title: "Load Layers Map"
fetched_at: "2026-05-12T19:34:35.762Z"
---
Load Layers Map. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Loads the elements contained in the requested layers of a Gaia map. The response includes the geometries associated with the elements. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:map-read. Path parameters. The RID of a Gaia map. Query parameters. Enables the use of preview functionality. Request body. The set of layer IDs to load from a Gaia map. Response body. A mapping of the requested layer IDs to a Gaia layer. Any invalid layer IDs will be omitted from this field. Examples. Error responses.
