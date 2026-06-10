---
source_url: "https://www.palantir.com/docs/gotham/api/map-resources/maps/add-emls-to-map/"
title: "Add Enterprise Map Layers To Map \u2022 API Reference"
---
# Add Enterprise Map Layers To Map

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Add enterprise map layers to a map. If unknown enterprise map layers or enterprise map layers that don't 
satisfy the security requirements are provided, the entire request will fail. For each request, a new layer 
is created for each enterprise map layer provided, thus not idempotent.
Returns the IDs of the layers created.

**operationId:** v1.addEmlsToMap

**path:** /api/gotham/v1/maps/{mapRid}/layers/emls

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

The request body to add enterprise map layers to a map

**name:** AddEnterpriseMapLayersToMapRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| emlIds | listType | False | The IDs of the enterprise map layers to be added to the map. |

**example:** {"emlIds":["0123456789012345678901234567890123456789012345678901234567890123",1234567890123456789012345678901234567890123456789012345678901234]}

### Response

#### Body

Success response.

**name:** AddEnterpriseMapLayersToMapResponse

**example:** {"dataLayerIds":["exampleLayerId"]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| dataLayerIds | listType | False |  |

**example:** {"dataLayerIds":["exampleLayerId"]}
