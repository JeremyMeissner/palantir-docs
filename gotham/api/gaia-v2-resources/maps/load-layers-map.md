---
source_url: "https://www.palantir.com/docs/gotham/api/gaia-v2-resources/maps/load-layers-map/"
title: "Load Layers Map \u2022 API Reference"
---
# Load Layers Map

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Loads the elements contained in the requested layers of a Gaia map. The response includes the geometries 
associated with the elements.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:map-read`.

**operationId:** v2.loadLayersMap

**path:** /api/v2/gaia/maps/{mapRid}/loadLayers

### Operation Type

### Scopes

| name |
| --- |
| api:map-read |

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

**name:** LoadLayersMapRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| layerIds | listType | False | The set of layer IDs to load from a Gaia map. |

**example:** {"layerIds":[1,2,3]}

### Response

#### Body

**name:** LoadLayersResponse

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| layers | mapType | False | A mapping of the requested layer IDs to a Gaia layer. Any invalid layer IDs will be omitted from this field. |

### Error Responses

| name | description |
| --- | --- |
| LoadLayersMapPermissionDenied | Could not loadLayers the Map. |
