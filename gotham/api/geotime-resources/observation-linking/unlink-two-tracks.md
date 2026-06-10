---
source_url: "https://www.palantir.com/docs/gotham/api/geotime-resources/observation-linking/unlink-two-tracks/"
title: "Unlink tracks \u2022 API Reference"
---
# Unlink tracks

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Unlinks a Geotime Track from another Track, removing any "pointers" between the Tracks.

**operationId:** v1.unlinkTracks

**path:** /api/gotham/v1/tracks/unlinkTracks

### Operation Type

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

A request to unlink a Geotime Track from another Track.

**name:** UnlinkTracksRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| trackRid | stringType | True | Globally unique identifier for a Geotime Track. This is synonymous with a Gotham Identifier and contains information like SourceSystemId, CollectionId, SpecId and TrackId. |
| otherTrackRid | stringType | True | Globally unique identifier for a Geotime Track. This is synonymous with a Gotham Identifier and contains information like SourceSystemId, CollectionId, SpecId and TrackId. |

**example:** [{"trackRid":"ri.gotham.1-1.geotime-track.foo.bar.baz.track0","otherTrackRid":"ri.gotham.1-1.geotime-track.foo.bar.baz.track1"}]

### Response

#### Body

A successful response means that the Tracks have been unlinked.

**name:** EmptySuccessResponse
