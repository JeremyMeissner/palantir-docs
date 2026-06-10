---
source_url: "https://www.palantir.com/docs/foundry/api/v2/media-sets-v2-resources/media-sets/get-transformation-job-result/"
parquet_url: "/foundry/api/v2/media-sets-v2-resources/media-sets/get-transformation-job-result/"
title: "Get Transformation Job Result"
fetched_at: "2026-05-12T19:34:37.768Z"
---
Get Transformation Job Result. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Gets the result of a completed transformation job. Returns the transformed media content as binary data. This endpoint will return an error if the transformation job has not completed successfully. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:mediasets-transform. Path parameters. The RID of the media set. The RID of the media item. The ID of the transformation job. Query parameters. A boolean flag that, when set to true, enables the use of beta features in preview mode. Response body. The transformed media content. Examples.
