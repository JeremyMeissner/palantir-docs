---
source_url: "https://www.palantir.com/docs/foundry/api/v2/filesystem-v2-resources/projects/list-organizations-of-project/"
title: "List Organizations Of Project"
---
# List Organizations Of Project

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. List of Organizations directly applied to a Project. The number of Organizations on a Project is typically small so the pageSize and pageToken parameters are not required. Path parameters. The unique resource identifier (RID) of a Project. Query parameters. The page size to use for the endpoint. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Enables the use of preview functionality. Response body. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Examples. Error responses.
