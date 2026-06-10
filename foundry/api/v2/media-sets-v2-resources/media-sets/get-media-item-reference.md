---
source_url: "https://www.palantir.com/docs/foundry/api/v2/media-sets-v2-resources/media-sets/get-media-item-reference/"
title: "Get Media Item Reference"
---
# Get Media Item Reference

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Gets the media reference for this media item. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:mediasets-read. Path parameters. The RID of the media set. The RID of the media item. Query parameters. A boolean flag that, when set to true, enables the use of beta features in preview mode. Response body. The representation of a media reference. The media type of the file or attachment. Examples: application/json, application/pdf, application/octet-stream, image/jpeg. A union of the types supported by media reference properties. Examples.
