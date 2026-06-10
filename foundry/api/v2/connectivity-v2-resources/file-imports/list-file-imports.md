---
source_url: "https://www.palantir.com/docs/foundry/api/v2/connectivity-v2-resources/file-imports/list-file-imports/"
title: "List File Imports"
---
# List File Imports

Lists all file imports defined for this connection. Only file imports that the user has permissions to view will be returned. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:connectivity-file-import-read. Path parameters. The Resource Identifier (RID) of a Connection (also known as a source). Query parameters. The page size to use for the endpoint. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Response body. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Examples. Error responses.
