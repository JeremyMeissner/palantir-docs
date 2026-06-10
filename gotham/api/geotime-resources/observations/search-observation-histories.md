---
source_url: "https://www.palantir.com/docs/gotham/api/geotime-resources/observations/search-observation-histories/"
title: "Search observation histories \u2022 API Reference"
---
# Search observation histories

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Returns Observation histories for Geotime Tracks matching the supplied query, clipped to a specified
time window. This endpoint has two distinct time filters that serve different purposes:

* `query.time` determines which Tracks are returned — only Tracks whose most recent Observation
  falls within that range are included.
* `historyWindow` determines how much history is returned for each matched Track — observations
  outside this window are excluded from the response.

These filters are independent and can be set to different ranges. If historyWindow is omitted,
it defaults to the past 7 days. All results are constrained to Observations conforming to the
specified Observation Spec.

**operationId:** v1.searchObservationHistories

**path:** /api/gotham/v1/observations/history/{observationSpecId}/search

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| observationSpecId | stringType | True | Search results will be constrained to Observations conforming to this Observation Spec. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

**name:** SearchObservationHistoryRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| query | objectType | True | The query to match to Geotime Tracks. |
| historyWindow | objectType | False | Filters which Tracks appear in results. Only Tracks whose most recent Observation has a timestamp within this inclusive range will be matched. Defaults to 7 days if not set. This does not affect how much history is returned for matched Tracks — use `historyWindow` for that. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and populate the next request's `pageToken` field with it. |

**example:** {"query":{"time":{"start":"2023-01-01T12:00:00Z","end":"2023-03-07T12:10:00Z"},"historyWindow":{"start":"2023-03-07T12:00:00Z","end":"2023-03-07T12:10:00Z"}}}

### Response

#### Body

Success response

**name:** SearchObservationHistoryResponse

**example:** {"data":{"trackRid":"ri.gotham-1.1.foo.bar.baz.track0","observations":[{"sourceSystemId":"foo","collectionId":"bar","observationSpecId":"baz","trackId":"track0","position":{"longitude":0.0,"latitude":0.0},"timestamp":"2023-03-05T17:00:00Z","name":"name0","staticProperties":[],"liveProperties":[]},{"sourceSystemId":"foo","collectionId":"bar","observationSpecId":"baz","trackId":"track0","position":{"longitude":11.0,"latitude":1.0},"timestamp":"2023-03-05T17:10:00Z","name":"name0","staticProperties":[],"liveProperties":[]}]}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and populate the next request's `pageToken` field with it. |

**example:** {"data":{"trackRid":"ri.gotham-1.1.foo.bar.baz.track0","observations":[{"sourceSystemId":"foo","collectionId":"bar","observationSpecId":"baz","trackId":"track0","position":{"longitude":0.0,"latitude":0.0},"timestamp":"2023-03-05T17:00:00Z","name":"name0","staticProperties":[],"liveProperties":[]},{"sourceSystemId":"foo","collectionId":"bar","observationSpecId":"baz","trackId":"track0","position":{"longitude":11.0,"latitude":1.0},"timestamp":"2023-03-05T17:10:00Z","name":"name0","staticProperties":[],"liveProperties":[]}]}}
