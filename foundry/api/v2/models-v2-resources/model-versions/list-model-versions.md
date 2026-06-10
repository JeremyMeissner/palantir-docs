---
source_url: "https://www.palantir.com/docs/foundry/api/v2/models-v2-resources/model-versions/list-model-versions/"
title: "List Model Versions"
---
# List Model Versions

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Lists all Model Versions for a given Model. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:models-read. Path parameters. The Resource Identifier (RID) of a Model. Query parameters. The branch to list versions from. Defaults to master on most enrollments. The page size to use for the endpoint. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Enables the use of preview functionality. Response body. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Examples. Error responses.
