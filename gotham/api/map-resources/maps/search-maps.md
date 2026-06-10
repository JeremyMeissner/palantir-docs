---
source_url: "https://www.palantir.com/docs/gotham/api/map-resources/maps/search-maps/"
title: "Search Maps \u2022 API Reference"
---
# Search Maps

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Retrieves all published maps containing the mapName (does not have to be exact).

**operationId:** v1.searchMaps

**path:** /api/gotham/v1/maps

### Operation Type

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |
| mapName | stringType | True | The name of the map(s) to be queried. |
| pageSize | integerType | False | The maximum number of matching Gaia maps to return. Defaults to 50. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. |

### Response

#### Body

Success response.

**name:** SearchMapsResponse

**example:** {"results":[{"mapRid":"ri..map.a1A2bcD3e45fg6h7ij","name":"Example Map Name","createAt":"2023-03-21T01:14:20.326Z","lastModified":"2023-03-23T17:38:29.323Z","numLayers":1,"numElements":5}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| results | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and populate the next request's `pageToken` field with it. |

**example:** {"results":[{"mapRid":"ri..map.a1A2bcD3e45fg6h7ij","name":"Example Map Name","createAt":"2023-03-21T01:14:20.326Z","lastModified":"2023-03-23T17:38:29.323Z","numLayers":1,"numElements":5}]}
