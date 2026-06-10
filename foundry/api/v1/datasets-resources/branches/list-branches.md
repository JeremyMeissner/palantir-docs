---
source_url: "https://www.palantir.com/docs/foundry/api/v1/datasets-resources/branches/list-branches/"
title: "List Branches"
---
# List Branches

Lists the Branches of a Dataset. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:datasets-read. Path parameters. The Resource Identifier (RID) of the Dataset on which to list Branches. Query parameters. The desired size of the page to be returned. Defaults to 1,000. See page sizes for details. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Response body. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. The list of branches in the current page. Examples. Error responses.
