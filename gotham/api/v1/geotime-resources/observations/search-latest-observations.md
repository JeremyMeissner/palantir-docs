---
source_url: "https://www.palantir.com/docs/gotham/api/v1/geotime-resources/observations/search-latest-observations/"
title: "Search latest observations"
---
# Search latest observations

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Gets the latest Observation along each Geotime Track matching the supplied query. Only returns Observations conforming to the given Observation Spec. Path parameters. Search results will be constrained to Observations conforming to this Observation Spec. Query parameters. Represents a boolean value that restricts an endpoint to preview mode when set to true. Request body. The query to match to Geotime Tracks. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and populate the next request's pageToken field with it. Response body. Success response. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and populate the next request's pageToken field with it. Examples.
