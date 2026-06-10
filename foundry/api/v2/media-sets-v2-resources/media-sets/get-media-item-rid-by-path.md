---
source_url: "https://www.palantir.com/docs/foundry/api/v2/media-sets-v2-resources/media-sets/get-media-item-rid-by-path/"
parquet_url: "/foundry/api/v2/media-sets-v2-resources/media-sets/get-media-item-rid-by-path/"
title: "Get Media Item Rid By Path"
fetched_at: "2026-05-12T19:34:37.759Z"
---
Get Media Item Rid By Path. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Returns the media item RID for the media item with the specified path. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:mediasets-read. Path parameters. The RID of the media set. Query parameters. The path of the media item. Specifies the specific branch by name in which to search for this media item. May not be provided if branch rid or view rid are provided. Specifies the specific branch by rid in which to search for this media item. May not be provided if branch name or view rid are provided. Specifies the specific view by rid in which to search for this media item. May not be provided if branch name or branch rid are provided. A boolean flag that, when set to true, enables the use of beta features in preview mode. Response body. The Resource Identifier (RID) of an individual Media Item within a Media Set in Foundry. Examples.
