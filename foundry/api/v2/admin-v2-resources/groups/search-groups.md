---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/groups/search-groups/"
title: "Search Groups"
---
# Search Groups

Perform a case-insensitive prefix search for groups based on group name. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-read. Request body. The page size to use for the endpoint. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Response body. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Examples. Error responses.
