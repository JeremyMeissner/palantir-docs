---
source_url: "https://www.palantir.com/docs/foundry/api/v2/media-sets-v2-resources/media-sets/get-media-set/"
parquet_url: "/foundry/api/v2/media-sets-v2-resources/media-sets/get-media-set/"
title: "Get Media Set"
fetched_at: "2026-05-12T19:34:37.759Z"
---
Get Media Set. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Gets information about the media set. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:mediasets-read. Path parameters. The Resource Identifier (RID) of a Media Set in Foundry. Query parameters. A boolean flag that, when set to true, enables the use of beta features in preview mode. Response body. Information about a media set. The Resource Identifier (RID) of a Media Set in Foundry. The schema type of a media set, indicating what type of media items it can contain. Enum values: AUDIO, DICOM, DOCUMENT, IMAGERY, MODEL_3D, MULTIMODAL, SPREADSHEET, STREAMING_VIDEO, VIDEO, EMAIL. A name for a media set branch. Valid branch names must be (a) non-empty, (b) less than 256 characters, and (c) not a valid ResourceIdentifier. The transaction policy for a media set, determining how writes are handled. Whether media items in this media set require paths. Examples.
