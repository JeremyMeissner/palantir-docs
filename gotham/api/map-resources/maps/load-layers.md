---
source_url: "https://www.palantir.com/docs/gotham/api/map-resources/maps/load-layers/"
title: "Load Map Layers \u2022 API Reference"
---
# Load Map Layers

## Endpoint

Loads the elements contained in the requested layers of a Gaia map. The response includes the geometries 
associated with the elements.

**operationId:** v1.loadLayers

**path:** /api/gotham/v1/maps/load/{mapGid}/layers

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mapGid | stringType | True | The GID of the map containing the layers to be loaded. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

**name:** LoadLayersRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| layerIds | listType | False | The set of layer IDs to load from a Gaia map. |
| includeDisplayFields | booleanType | False | If set to true, the response will include generic fields associated with a Gaia element. Note that  this does not guarantee that all element fields will be included; fields are loaded on a best effort basis. Defaults to false. |

**example:** {"layerIds":["exampleLayerId"]}

### Response

#### Body

A successful load layers response.

**name:** LoadLayersResponse

**example:** {"layers":{"exampleLayerId":{"id":"exampleLayerId","elements":[{"id":"exampleElementId","parentId":"exampleLayerId","features":[{"geometry":{"type":"Point","coordinates":[0,0]},"style":{"label":{"text":"sample-text","textRotation":40.1,"textColor":"#000000","textAlignment":"RIGHT"}}},{"geometry":{"type":"Point","coordinates":[0,0]}}]}]}}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| layers | mapType | False | A mapping of the requested layer IDs to a Gaia layer. Any invalid layer IDs will be omitted from this field. |

**example:** {"layers":{"exampleLayerId":{"id":"exampleLayerId","elements":[{"id":"exampleElementId","parentId":"exampleLayerId","features":[{"geometry":{"type":"Point","coordinates":[0,0]},"style":{"label":{"text":"sample-text","textRotation":40.1,"textColor":"#000000","textAlignment":"RIGHT"}}},{"geometry":{"type":"Point","coordinates":[0,0]}}]}]}}}
