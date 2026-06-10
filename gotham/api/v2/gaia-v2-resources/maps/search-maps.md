---
source_url: "https://www.palantir.com/docs/gotham/api/v2/gaia-v2-resources/maps/search-maps/"
title: "Search Maps"
---
# Search Maps

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Retrieves all published maps containing the mapName (does not have to be exact). Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:map-read. Query parameters. The name of the map(s) to be queried. The maximum number of matching Gaia maps to return. Defaults to 50. The page token indicates where to start paging. This should be omitted from the first page's request. Enables the use of preview functionality. Response body. The response body containing the queried Gaia maps. The page token indicates where to start paging. api-gateway's Core.PageToken is an immutable @Unsafe String, which is incompatible with Gaia's backend search. This is a custom PageToken that is an immutable @Safe String. Examples. Error responses.
