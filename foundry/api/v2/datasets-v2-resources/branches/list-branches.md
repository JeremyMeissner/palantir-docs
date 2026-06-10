---
source_url: "https://www.palantir.com/docs/foundry/api/v2/datasets-v2-resources/branches/list-branches/"
title: "List Branches"
---
# List Branches

Lists the Branches of a Dataset. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:datasets-read. Path parameters. The Resource Identifier (RID) of a Dataset. Query parameters. The page size to use for the endpoint. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Response body. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Examples. Error responses.
