---
source_url: "https://www.palantir.com/docs/foundry/api/v2/filesystem-v2-resources/resources/list-markings-of-resource/"
title: "List Markings Of Resource"
---
# List Markings Of Resource

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. List of Markings directly applied to a resource. The number of Markings on a resource is typically small so the pageSize and pageToken parameters are not required. Path parameters. The unique resource identifier (RID) of a Resource. Query parameters. The page size to use for the endpoint. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Enables the use of preview functionality. Response body. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Examples. Error responses.
