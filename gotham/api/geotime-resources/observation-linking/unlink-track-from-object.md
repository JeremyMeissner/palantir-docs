---
source_url: "https://www.palantir.com/docs/gotham/api/geotime-resources/observation-linking/unlink-track-from-object/"
title: "Unlink track from object \u2022 API Reference"
---
# Unlink track from object

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Unlinks a Geotime Track from an Object, by ensuring that we remove any "pointers" between the Track and Object

**operationId:** v1.unlinkTrackAndObject

**path:** /api/gotham/v1/tracks/unlinkFromObject

### Operation Type

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

A request to unlink a Geotime Track from an Object

**name:** UnlinkTrackAndObjectRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| trackRid | stringType | True | Globally unique identifier for a Geotime Track. This is synonymous with a Gotham Identifier and contains information like SourceSystemId, CollectionId, SpecId and TrackId. |
| objectRid | stringType | True | Globally unique identifier for an Object Rid. |

**example:** [{"trackRid":"ri.gotham.1-1.geotime-track.foo.bar.baz.track0","objectRid":"ri.gotham.1-1.object.someString"}]

### Response

#### Body

A successful response means that the Track has been unlinked from the Object.

**name:** EmptySuccessResponse
