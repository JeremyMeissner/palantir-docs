---
source_url: "https://www.palantir.com/docs/gotham/api/v1/geotime-resources/observation-linking/unlink-two-tracks/"
parquet_url: "/gotham/api/v1/geotime-resources/observation-linking/unlink-two-tracks/"
title: "Unlink tracks"
fetched_at: "2026-05-12T19:34:35.748Z"
---
Unlink tracks. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Unlinks a Geotime Track from another Track, removing any "pointers" between the Tracks. Query parameters. Represents a boolean value that restricts an endpoint to preview mode when set to true. Request body. A request to unlink a Geotime Track from another Track. Globally unique identifier for a Geotime Track. This is synonymous with a Gotham Identifier and contains information like SourceSystemId, CollectionId, SpecId and TrackId. Globally unique identifier for a Geotime Track. This is synonymous with a Gotham Identifier and contains information like SourceSystemId, CollectionId, SpecId and TrackId. Response body. A successful response means that the Tracks have been unlinked. Examples.
