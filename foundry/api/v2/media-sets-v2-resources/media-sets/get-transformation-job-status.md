---
source_url: "https://www.palantir.com/docs/foundry/api/v2/media-sets-v2-resources/media-sets/get-transformation-job-status/"
parquet_url: "/foundry/api/v2/media-sets-v2-resources/media-sets/get-transformation-job-status/"
title: "Get Transformation Job Status"
fetched_at: "2026-05-12T19:34:37.769Z"
---
Get Transformation Job Status. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Gets the status of a transformation job. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:mediasets-transform. Path parameters. The RID of the media set. The RID of the media item. The ID of the transformation job. Query parameters. A boolean flag that, when set to true, enables the use of beta features in preview mode. Response body. The status of the transformation job. The status of a transformation job. Enum values: PENDING, FAILED, SUCCESSFUL. An identifier for a media item transformation job. Examples.
