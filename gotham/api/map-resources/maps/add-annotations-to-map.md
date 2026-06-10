---
source_url: "https://www.palantir.com/docs/gotham/api/map-resources/maps/add-annotations-to-map/"
title: "Add Annotations To Map \u2022 API Reference"
---
# Add Annotations To Map

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Add annotations to a map. Currently only Line, Polygon, Rectangle, Point, and tactical graphic annotations 
may be added. If any provided parameters are unknown, invalid, or do not satisfy the security requirements,
the entire request will fail.
For each request, a new element is created for each annotation, as well as a new layer if no parent layer 
is specified; thus not idempotent.
Returns the ID of the layer created.

**operationId:** v1.addAnnotationsToMap

**path:** /api/gotham/v1/maps/{mapRid}/layers/annotations

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mapRid | stringType | True | The RID of the Gaia map that you wish to add annotations to. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

The request body to add annotations to a map

**name:** AddAnnotationsToMapRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| parentLayerId | stringType | False | The ID of a layer in a Gaia map. |
| layerLabel | stringType | False | If provided AND no existing parentLayerId is provided, the new layer created will be set with the provided label. |
| annotations | listType | False | The annotations to be added to the map. |

**example:** {"layerLabel":"Example layer name.","annotations":[{"title":"Example line annotation name.","annotationDescription":"Example description.","annotationType":{"type":"LineAnnotation","coordinates":[{"lon":0,"lat":0},{"lon":1,"lat":1},{"lon":2,"lat":2}]},"style":{"fill":{"opacity":0.5,"color":"#000000"}}}]}

### Response

#### Body

Success response.

**name:** AddAnnotationsToMapResponse

**example:** {"parentLayerId":"exampleLayerId","annotationIds":["exampleAnnotationId1","exampleAnnotationId2"]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| parentLayerId | stringType | True | The ID of a layer in a Gaia map. |
| annotationIds | listType | False | The IDs of the created annotations |

**example:** {"parentLayerId":"exampleLayerId","annotationIds":["exampleAnnotationId1","exampleAnnotationId2"]}
