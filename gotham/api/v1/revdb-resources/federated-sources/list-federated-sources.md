---
source_url: "https://www.palantir.com/docs/gotham/api/v1/revdb-resources/federated-sources/list-federated-sources/"
title: "List federated sources"
---
# List federated sources

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Get a list of all federated sources. Query parameters. Represents a boolean value that restricts an endpoint to preview mode when set to true. Response body. A list of federated sources. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and populate the next request's pageToken field with it. Examples.
