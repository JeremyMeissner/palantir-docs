---
source_url: "https://www.palantir.com/docs/gotham/api/v1/revdb-resources/resolution/get-resolution-metadata/"
parquet_url: "/gotham/api/v1/revdb-resources/resolution/get-resolution-metadata/"
title: "Get resolution metadata"
fetched_at: "2026-05-12T19:34:35.739Z"
---
Get resolution metadata. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Get metadata from previously-performed resolutions. If the object has not been resolved, the canonicalObjectPrimaryKey and winnerObjectPrimaryKey will be identical, and the otherObjectPrimaryKeys will be empty. Path parameters. The primary key of the requested object. Query parameters. Represents a boolean value that restricts an endpoint to preview mode when set to true. Response body. The resolution metadata the resolved object. The primary key/unique identifier of an object, useful for interacting with Gotham APIs to load and mutate objects. The primary key/unique identifier of an object, useful for interacting with Gotham APIs to load and mutate objects. All other sub-objects which compose this resolved object. This may include other winner object keys if some sub-objects have themselves been resolved. Examples.
