---
source_url: "https://www.palantir.com/docs/gotham/api/geotime-resources/observation-linking/link-two-tracks/"
title: "Link tracks \u2022 API Reference"
---
# Link tracks

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Links a Geotime Track with another Track, by ensuring that the Tracks have "pointers" to each other.

**operationId:** v1.linkTracks

**path:** /api/gotham/v1/tracks/linkTracks

### Operation Type

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

A request to link a Geotime Track to another Track

**name:** LinkTracksRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| trackRid | stringType | True | Globally unique identifier for a Geotime Track. This is synonymous with a Gotham Identifier and contains information like SourceSystemId, CollectionId, SpecId and TrackId. |
| otherTrackRid | stringType | True | Globally unique identifier for a Geotime Track. This is synonymous with a Gotham Identifier and contains information like SourceSystemId, CollectionId, SpecId and TrackId. |

**example:** [{"trackRid":"ri.gotham.1-1.geotime-track.foo.bar.baz.track0","otherTrackRid":"ri.gotham.1-1.geotime-track.foo.bar.baz.track1"}]

### Response

#### Body

A successful response means that the Tracks have been linked.

**name:** EmptySuccessResponse
