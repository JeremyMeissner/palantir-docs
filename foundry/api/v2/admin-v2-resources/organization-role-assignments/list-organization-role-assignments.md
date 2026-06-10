---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/organization-role-assignments/list-organization-role-assignments/"
parquet_url: "/foundry/api/v2/admin-v2-resources/organization-role-assignments/list-organization-role-assignments/"
title: "List Organization Role Assignments"
fetched_at: "2026-05-12T19:34:37.733Z"
---
List Organization Role Assignments. List all principals who are assigned a role for the given Organization. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-read. Path parameters. Response body. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Examples. Error responses.
