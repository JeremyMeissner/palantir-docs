---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/groups/list-groups/"
title: "List Groups"
---
# List Groups

Lists all Groups. This is a paged endpoint. Each page may be smaller or larger than the requested page size. However, it is guaranteed that if there are more results available, the nextPageToken field will be populated. To get the next page, make the same request again, but set the value of the pageToken query parameter to be value of the nextPageToken value of the previous response. If there is no nextPageToken field in the response, you are on the last page. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-read. Query parameters. The page size to use for the endpoint. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Response body. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Examples. Error responses.
