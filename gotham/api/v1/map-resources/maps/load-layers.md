---
source_url: "https://www.palantir.com/docs/gotham/api/v1/map-resources/maps/load-layers/"
parquet_url: "/gotham/api/v1/map-resources/maps/load-layers/"
title: "Load Map Layers"
fetched_at: "2026-05-12T19:34:35.730Z"
---
Load Map Layers. Loads the elements contained in the requested layers of a Gaia map. The response includes the geometries associated with the elements. Path parameters. The GID of the map containing the layers to be loaded. Query parameters. Represents a boolean value that restricts an endpoint to preview mode when set to true. Request body. The set of layer IDs to load from a Gaia map. If set to true, the response will include generic fields associated with a Gaia element. Note that this does not guarantee that all element fields will be included; fields are loaded on a best effort basis. Defaults to false. Response body. A successful load layers response. A mapping of the requested layer IDs to a Gaia layer. Any invalid layer IDs will be omitted from this field. Examples.
