---
source_url: "https://www.palantir.com/docs/gotham/api/geotime-resources/observations/search-latest-observations/"
title: "Search latest observations \u2022 API Reference"
---
# Search latest observations

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Gets the latest Observation along each Geotime Track matching the supplied query. Only returns Observations
conforming to the given Observation Spec.

**operationId:** v1.searchLatestObservations

**path:** /api/gotham/v1/observations/latest/{observationSpecId}/search

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

**name:** SearchLatestObservationsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| query | objectType | True | The query to match to Geotime Tracks. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and populate the next request's `pageToken` field with it. |

**example:** {"query":{"time":{"start":"2023-01-01T12:00:00Z","end":"2023-03-07T12:10:00Z"}}}

### Response

#### Body

Success response

**name:** SearchLatestObservationsResponse

**example:** [{"sourceSystemId":"foo","collectionId":"bar","observationSpecId":"baz","trackId":"track0","position":{"longitude":0.0,"latitude":0.0},"timestamp":"2023-03-05T17:00:00Z","name":"name0","staticProperties":[],"liveProperties":[{"propertyType":"liveProperty","value":0.0}]},{"sourceSystemId":"foo","collectionId":"bar","observationSpecId":"baz","trackId":"track1","position":{"longitude":11.0,"latitude":1.0},"timestamp":"2023-03-05T17:10:00Z","name":"name1","staticProperties":[],"liveProperties":[]}]

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and populate the next request's `pageToken` field with it. |

**example:** [{"sourceSystemId":"foo","collectionId":"bar","observationSpecId":"baz","trackId":"track0","position":{"longitude":0.0,"latitude":0.0},"timestamp":"2023-03-05T17:00:00Z","name":"name0","staticProperties":[],"liveProperties":[{"propertyType":"liveProperty","value":0.0}]},{"sourceSystemId":"foo","collectionId":"bar","observationSpecId":"baz","trackId":"track1","position":{"longitude":11.0,"latitude":1.0},"timestamp":"2023-03-05T17:10:00Z","name":"name1","staticProperties":[],"liveProperties":[]}]
