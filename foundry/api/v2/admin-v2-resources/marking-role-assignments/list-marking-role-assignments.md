---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/marking-role-assignments/list-marking-role-assignments/"
parquet_url: "/foundry/api/v2/admin-v2-resources/marking-role-assignments/list-marking-role-assignments/"
title: "List Marking Role Assignments"
fetched_at: "2026-05-12T19:34:37.742Z"
---
List Marking Role Assignments. List all principals who are assigned a role for the given Marking. Ignores the pageSize parameter. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-read. Path parameters. The ID of a security marking. Query parameters. The page size to use for the endpoint. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Response body. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Examples. Error responses.
