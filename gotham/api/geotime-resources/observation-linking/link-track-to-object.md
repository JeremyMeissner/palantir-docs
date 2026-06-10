---
source_url: "https://www.palantir.com/docs/gotham/api/geotime-resources/observation-linking/link-track-to-object/"
title: "Link track to object \u2022 API Reference"
---
# Link track to object

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Links a Geotime Track with an Object, by ensuring that the Track has a "pointer"
to its Object, and vice versa.

**operationId:** v1.linkTrackAndObject

**path:** /api/gotham/v1/tracks/linkToObject

### Operation Type

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

A request to link a Geotime Track to an Object

**name:** LinkTrackAndObjectRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| trackRid | stringType | True | Globally unique identifier for a Geotime Track. This is synonymous with a Gotham Identifier and contains information like SourceSystemId, CollectionId, SpecId and TrackId. |
| objectRid | stringType | True | Globally unique identifier for an Object Rid. |

**example:** [{"trackRid":"ri.gotham.1-1.geotime-track.foo.bar.baz.track0","objectRid":"ri.gotham.1-1.object.someString"}]

### Response

#### Body

A successful response means that the Track has been linked to the Object.

**name:** EmptySuccessResponse
