---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/users/search-users/"
parquet_url: "/foundry/api/v2/admin-v2-resources/users/search-users/"
title: "Search Users"
fetched_at: "2026-05-12T19:34:37.708Z"
---
Search Users. Perform a case-insensitive prefix search for active users based on username, given name and family name. Deleted users are not included in results. To list deleted users, use the list endpoint with include=DELETED. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-read. Request body. The page size to use for the endpoint. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Response body. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Examples. Error responses.
