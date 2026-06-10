---
source_url: "https://www.palantir.com/docs/foundry/api/v2/orchestration-v2-resources/builds/list-jobs-of-build/"
title: "List Jobs Of Build"
---
# List Jobs Of Build

Get the Jobs in the Build. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:orchestration-read. Path parameters. The RID of a Build. Query parameters. The page size to use for the endpoint. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Response body. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Examples.
