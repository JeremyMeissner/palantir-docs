---
source_url: "https://www.palantir.com/docs/gotham/api/v1/map-resources/maps/load-map-extension/"
title: "Load a Map With Metadata"
---
# Load a Map With Metadata

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Same as /v1/maps/load/{mapGid}, but allows you to pass in a request body for further configuration. Loads the structure and basic metadata of a Gaia map, given a map GID. Metadata includes the map's title and layer labels. The response contains a mapping of all layers contained in the map. The map's layer hierarchy can be recreated by using the rootLayerIds in the response along with the subLayerIds field in the layer's metadata. Path parameters. The GID of the map to be loaded. Query parameters. Represents a boolean value that restricts an endpoint to preview mode when set to true. Request body. Response body. A successful map load response. The title of the loaded Gaia map. The root layers of the loaded Gaia map. This does not include sub-layers, i.e. layers nested within a parent layer in a Gaia map. A mapping of all the layers contained in the Gaia map. Includes layers nested under the root layers. Examples.
