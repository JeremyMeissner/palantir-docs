---
source_url: "https://www.palantir.com/docs/foundry/api/v2/filesystem-v2-resources/resources/get-by-path-resources-batch/"
title: "Get By Path Resources Batch"
---
# Get By Path Resources Batch

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Gets multiple Resources by their absolute paths. Returns a list of resources. If a path does not exist, is inaccessible, or refers to a root folder or space, it will not be included in the response. At most 1,000 paths should be requested at once. The maximum batch size for this endpoint is 1000. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:filesystem-read. Query parameters. Enables the use of preview functionality. Request body. Response body. Examples.
