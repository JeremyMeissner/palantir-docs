---
source_url: "https://www.palantir.com/docs/gotham/api/v1/geotime-resources/observations/write-observations/"
parquet_url: "/gotham/api/v1/geotime-resources/observations/write-observations/"
title: "Write observations"
fetched_at: "2026-05-12T19:34:35.753Z"
---
Write observations. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Writes Observations directly to Geotime. Returns the Observations that could not be written to Geotime with the reason for why they could not be written. Any Observations not in the response are guaranteed to have been written successfully to Geotime's backing data store. Query parameters. Represents a boolean value that restricts an endpoint to preview mode when set to true. Request body. The list of Observations to write to Geotime. A geotemporal object along a Geotime Track (SSID, CID, SpecID, TrackID quadruplet). Response body. Response with information about any Observations that failed to be written. Examples.
