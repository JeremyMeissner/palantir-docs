---
source_url: "https://www.palantir.com/docs/foundry/api/v2/media-sets-v2-resources/media-sets/read-original-media-item/"
title: "Read Original Media Item"
---
# Read Original Media Item

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Gets the content of an original file uploaded to the media item, even if it was transformed on upload due to being an additional input format. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:mediasets-read. Path parameters. The Resource Identifier (RID) of a Media Set in Foundry. The Resource Identifier (RID) of an individual Media Item within a Media Set in Foundry. Query parameters. A boolean flag that, when set to true, enables the use of beta features in preview mode. Response body. The content stream. Examples.
