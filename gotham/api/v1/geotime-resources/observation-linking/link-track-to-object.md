---
source_url: "https://www.palantir.com/docs/gotham/api/v1/geotime-resources/observation-linking/link-track-to-object/"
title: "Link track to object"
---
# Link track to object

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Links a Geotime Track with an Object, by ensuring that the Track has a "pointer" to its Object, and vice versa. Query parameters. Represents a boolean value that restricts an endpoint to preview mode when set to true. Request body. A request to link a Geotime Track to an Object. Globally unique identifier for a Geotime Track. This is synonymous with a Gotham Identifier and contains information like SourceSystemId, CollectionId, SpecId and TrackId. Globally unique identifier for an Object Rid. Response body. A successful response means that the Track has been linked to the Object. Examples.
