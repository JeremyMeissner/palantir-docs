---
source_url: "https://www.palantir.com/docs/gotham/api/v2/gaia-v2-resources/maps/load-map/"
title: "Load Map"
---
# Load Map

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Loads the structure and basic metadata of a Gaia map, given a map GID. Metadata includes the map's title and layer labels. The response contains a mapping of all layers contained in the map. The map's layer hierarchy can be recreated by using the rootLayerIds in the response along with the subLayerIds field in the layer's metadata. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:map-read. Path parameters. The RID of a Gaia map. Query parameters. Enables the use of preview functionality. Response body. Contains information related to a Gaia map's structure and basic metadata. The title of the loaded Gaia map. The root layers of the loaded Gaia map. This does not include sub-layers, i.e. layers nested within a parent layer in a Gaia map. A mapping of all the layers contained in the Gaia map. Includes layers nested under the root layers. Examples. Error responses.
