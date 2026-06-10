---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/enrollment-role-assignments/list-enrollment-role-assignments/"
parquet_url: "/foundry/api/v2/admin-v2-resources/enrollment-role-assignments/list-enrollment-role-assignments/"
title: "List Enrollment Role Assignments"
fetched_at: "2026-05-12T19:34:37.759Z"
---
List Enrollment Role Assignments. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. List all principals who are assigned a role for the given Enrollment. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-read. Path parameters. Query parameters. Enables the use of preview functionality. Response body. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Examples. Error responses.
