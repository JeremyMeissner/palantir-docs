---
source_url: "https://www.palantir.com/docs/foundry/api/v2/filesystem-v2-resources/resources/get-resources-batch/"
parquet_url: "/foundry/api/v2/filesystem-v2-resources/resources/get-resources-batch/"
title: "Get Resources Batch"
fetched_at: "2026-05-12T19:34:37.657Z"
---
Get Resources Batch. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Fetches multiple resources in a single request. Returns a map from RID to the corresponding resource. If a resource does not exist, or if it is a root folder or space, its RID will not be included in the map. At most 1,000 resources should be requested at once. The maximum batch size for this endpoint is 1000. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:filesystem-read. Query parameters. Enables the use of preview functionality. Request body. Response body. Examples.
