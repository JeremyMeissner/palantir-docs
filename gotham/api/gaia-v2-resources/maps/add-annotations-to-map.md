---
source_url: "https://www.palantir.com/docs/gotham/api/gaia-v2-resources/maps/add-annotations-to-map/"
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

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:map-write`.

**operationId:** v2.addAnnotationsToMap

**path:** /api/v2/gaia/maps/{mapRid}/addAnnotationsTo

### Operation Type

### Scopes

| name |
| --- |
| api:map-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mapRid | stringType | True | The RID of a Gaia map. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** AddAnnotationsToMapRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| parentLayerId | stringType | False | If provided, the created annotations will be nested under this layer ID. The layer ID must be an annotation layer that already exists. If not provided, a new layer will be created. |
| layerLabel | stringType | False | If provided AND no existing parentLayerId is provided, the new layer created will be set with the  provided label. |
| annotations | listType | False | The annotations to create on the map. |

**example:** {"layerLabel":"Example label","annotations":[{"title":"Example Point Annotation","annotationDescription":"An example point annotation","annotationType":{"type":"point","coordinate":{"lon":0.0,"lat":0.0},"symbol":{"type":"IconSymbol","id":"marker"}},"style":{"stroke":{"color":"#FFFFFF","width":2,"opacity":1.0}}}]}

### Response

#### Body

The response body to add annotations to a map, containing the ID of the created layer.

**name:** AddAnnotationsToMapResponse

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| parentLayerId | stringType | True | The annotation data layer ID containing the created annotations |
| annotationIds | listType | False |  |

### Error Responses

| name | description |
| --- | --- |
| ExpectedMapGid | Expected a map Gid. |
| AddAnnotationsToMapPermissionDenied | Could not addAnnotationsTo the Map. |
