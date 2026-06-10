---
source_url: "https://www.palantir.com/docs/gotham/api/map-resources/maps/add-objects-to-map/"
title: "Add Objects To Map \u2022 API Reference"
---
# Add Objects To Map

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Add objects to a map. Currently only Foundry-managed object types may be added. If unknown objects 
or objects that don't satisfy the security requirements are provided, the entire request will fail.
This creates a new layer that includes all the provided objects per request, thus not idempotent.
Returns the ID of the layer created.

**operationId:** v1.addObjectsToMap

**path:** /api/gotham/v1/maps/{mapRid}/layers/objects

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mapRid | stringType | True | The RID of the Gaia map that you wish to add objects to. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

The request body to add objects to a map.

**name:** AddObjectsToMapRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| objectRids | listType | False |  |
| label | stringType | True | The name of the layer to be created |

**example:** {"objectRids":["ri.phonograph2-objects.main.object.example1","ri.phonograph2-objects.main.object.example2"],"label":"Example layer name."}

### Response

#### Body

Success response.

**name:** AddObjectsToMapResponse

**example:** {"dataLayerIds":["exampleLayerId"]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| dataLayerIds | listType | False |  |

**example:** {"dataLayerIds":["exampleLayerId"]}
