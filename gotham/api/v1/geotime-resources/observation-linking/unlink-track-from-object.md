---
source_url: "https://www.palantir.com/docs/gotham/api/v1/geotime-resources/observation-linking/unlink-track-from-object/"
title: "Unlink track from object"
---
# Unlink track from object

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Unlinks a Geotime Track from an Object, by ensuring that we remove any "pointers" between the Track and Object. Query parameters. Represents a boolean value that restricts an endpoint to preview mode when set to true. Request body. A request to unlink a Geotime Track from an Object. Globally unique identifier for a Geotime Track. This is synonymous with a Gotham Identifier and contains information like SourceSystemId, CollectionId, SpecId and TrackId. Globally unique identifier for an Object Rid. Response body. A successful response means that the Track has been unlinked from the Object. Examples.
