---
source_url: "https://www.palantir.com/docs/gotham/api/v1/map-resources/maps/export-kmz/"
parquet_url: "/gotham/api/v1/map-resources/maps/export-kmz/"
title: "Export Map as KMZ"
fetched_at: "2026-05-12T19:34:35.729Z"
---
Export Map as KMZ. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Export all map elements from a Gaia map to a KMZ file suitable for rendering in external applications, such as Google Earth. There are no schema compatibility guarantees provided for internal KMZ content exported by this endpoint. Only local map elements will be exported i.e. no elements from linked maps. Path parameters. The artifact identifier of the Gaia map being exported, which can be copied via Help > Developer > Copy id. The export call will download all elements in the referenced map. Query parameters. Represents a boolean value that restricts an endpoint to preview mode when set to true. Request body. The request body to export elements to a KMZ/SHP file. The name of the exported file. Defaults to 'palantir-export'. Response body. Success response. Examples.
