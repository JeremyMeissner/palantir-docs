---
source_url: "https://www.palantir.com/docs/gotham/api/map-resources/maps/add-artifacts-to-map/"
title: "Add Artifacts To Map \u2022 API Reference"
---
# Add Artifacts To Map

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Add artifacts to a map. Currently only target collection artifacts may be added. If unknown artifacts
or artifacts that don't satisfy the security requirements are provided, the entire request will fail.
For each request, a new layer is created for each artifact, thus not idempotent.
Returns the IDs of the layers created.

**operationId:** v1.addArtifactsToMap

**path:** /api/gotham/v1/maps/{mapRid}/layers/artifacts

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mapRid | stringType | True | The RID of the Gaia map that you wish to add artifacts to. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

The request body to add artifacts to a map

**name:** AddArtifactsToMapRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| artifactGids | listType | False | The GIDs of the artifacts to be added to the map. |
| label | stringType | True | The name of the layer to be created |

**example:** {"artifactGids":["ri.gotham-artifact.instance.service-type.a1A2bcD3e45fg6h7ij"],"label":"Example layer name."}

### Response

#### Body

Success response.

**name:** AddArtifactsToMapResponse

**example:** {"dataLayerIds":["exampleLayerId"]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| dataLayerIds | listType | False |  |

**example:** {"dataLayerIds":["exampleLayerId"]}
