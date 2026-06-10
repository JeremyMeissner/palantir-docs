---
source_url: "https://www.palantir.com/docs/gotham/api/v1/map-resources/maps/search-maps/"
parquet_url: "/gotham/api/v1/map-resources/maps/search-maps/"
title: "Search Maps"
fetched_at: "2026-05-12T19:34:35.736Z"
---
Search Maps. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Retrieves all published maps containing the mapName (does not have to be exact). Query parameters. Represents a boolean value that restricts an endpoint to preview mode when set to true. The name of the map(s) to be queried. The maximum number of matching Gaia maps to return. Defaults to 50. The page token indicates where to start paging. This should be omitted from the first page's request. Response body. Success response. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and populate the next request's pageToken field with it. Examples.
