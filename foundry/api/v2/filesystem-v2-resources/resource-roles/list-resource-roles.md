---
source_url: "https://www.palantir.com/docs/foundry/api/v2/filesystem-v2-resources/resource-roles/list-resource-roles/"
title: "List Resource Roles"
---
# List Resource Roles

List the roles on a resource. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:filesystem-read. Path parameters. The unique resource identifier (RID) of a Resource. Query parameters. Whether to include inherited roles on the resource. The page size to use for the endpoint. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Response body. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Examples. Error responses.
