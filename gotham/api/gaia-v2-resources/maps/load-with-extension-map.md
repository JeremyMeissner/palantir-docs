---
source_url: "https://www.palantir.com/docs/gotham/api/gaia-v2-resources/maps/load-with-extension-map/"
title: "Load With Extension Map \u2022 API Reference"
---
# Load With Extension Map

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Same as /gotham/v1/maps/load/{mapGid}, but allows you to pass in a request body for further configuration.

Loads the structure and basic metadata of a Gaia map, given a map GID. Metadata includes the map's title and
layer labels.

The response contains a mapping of all layers contained in the map. The map's layer hierarchy can be recreated
by using the `rootLayerIds` in the response along with the `subLayerIds` field in the layer's metadata.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:map-read`.

**operationId:** v2.loadWithExtensionMap

**path:** /api/v2/gaia/maps/{mapRid}/loadWithExtension

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

**name:** LoadWithExtensionMapRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| extensions | objectType | True | Describes extensions that this API should apply to the loaded data |

### Response

#### Body

Contains information related to a Gaia map's structure and basic metadata.

**name:** LoadMapResponse

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| title | stringType | True | The title of the loaded Gaia map. |
| rootLayerIds | listType | False | The **root** layers of the loaded Gaia map. This does not include sub-layers, i.e. layers nested within a parent layer in a Gaia map. |
| layers | mapType | False | A mapping of **all** the layers contained in the Gaia map. Includes layers nested under the root layers. |

### Error Responses

| name | description |
| --- | --- |
| MapNotFound | Map not found |
| LoadWithExtensionMapPermissionDenied | Could not loadWithExtension the Map. |
