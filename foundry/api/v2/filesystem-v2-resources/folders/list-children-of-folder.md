---
source_url: "https://www.palantir.com/docs/foundry/api/v2/filesystem-v2-resources/folders/list-children-of-folder/"
title: "List Children Of Folder"
---
# List Children Of Folder

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. List all child Resources of the Folder. This is a paged endpoint. The page size will be limited to 2,000 results per page. If no page size is provided, this page size will also be used as the default. Path parameters. The unique resource identifier (RID) of a Folder. Query parameters. The page size to use for the endpoint. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Enables the use of preview functionality. Response body. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Examples. Error responses.
