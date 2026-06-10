---
source_url: "https://www.palantir.com/docs/gotham/api/map-resources/maps/load-map-extension/"
title: "Load a Map With Metadata \u2022 API Reference"
---
# Load a Map With Metadata

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Same as /v1/maps/load/{mapGid}, but allows you to pass in a request body for further configuration.

Loads the structure and basic metadata of a Gaia map, given a map GID. Metadata includes the map's title and 
layer labels.

The response contains a mapping of all layers contained in the map. The map's layer hierarchy can be recreated 
by using the `rootLayerIds` in the response along with the `subLayerIds` field in the layer's metadata.

**operationId:** v1.loadMapWithExtension

**path:** /api/gotham/v1/maps/loadWithExtension/{mapGid}

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mapGid | stringType | True | The GID of the map to be loaded. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

**name:** LoadMapRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| extensions | objectType | False |  |

**example:** {"extensions":{"foundryObjectSet":{}}}

### Response

#### Body

A successful map load response.

**name:** LoadMapResponse

**example:** {"title":"Example Gaia Map Title","rootLayerIds":["exampleRootLayerId"],"layers":{"exampleRootLayerId":{"id":"exampleRootLayerId","subLayerIds":["exampleNestedLayerId"],"label":"Root layer label"},"exampleNestedLayerId":{"id":"exampleNestedLayerId","label":"Nested layer label"}}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| title | stringType | True | The title of the loaded Gaia map. |
| rootLayerIds | listType | False | The **root** layers of the loaded Gaia map. This does not include sub-layers, i.e. layers nested within a parent layer in a Gaia map. |
| layers | mapType | False | A mapping of **all** the layers contained in the Gaia map. Includes layers nested under the root layers. |

**example:** {"title":"Example Gaia Map Title","rootLayerIds":["exampleRootLayerId"],"layers":{"exampleRootLayerId":{"id":"exampleRootLayerId","subLayerIds":["exampleNestedLayerId"],"label":"Root layer label"},"exampleNestedLayerId":{"id":"exampleNestedLayerId","label":"Nested layer label"}}}
