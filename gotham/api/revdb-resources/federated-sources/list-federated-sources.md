---
source_url: "https://www.palantir.com/docs/gotham/api/revdb-resources/federated-sources/list-federated-sources/"
title: "List federated sources \u2022 API Reference"
---
# List federated sources

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Get a list of all federated sources.

**operationId:** v1.listFederatedSources

**path:** /api/gotham/v1/federatedSources

### Operation Type

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Response

#### Body

A list of federated sources.

**name:** GetFederatedSourceResponse

**example:** [{"name":"My Federated Source"},{"name":"My Other Federated Source"}]

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and populate the next request's `pageToken` field with it. |
| data | listType | False |  |

**example:** [{"name":"My Federated Source"},{"name":"My Other Federated Source"}]
