---
source_url: "https://www.palantir.com/docs/gotham/api/gaia-v2-resources/maps/add-artifacts-to-map/"
title: "Add Artifacts To Map \u2022 API Reference"
---
# Add Artifacts To Map

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Add artifacts to a map. Currently only Foundry-managed object types may be added. If unknown objects
or objects that don't satisfy the security requirements are provided, the entire request will fail.
This creates a new layer that includes all the provided objects per request, thus not idempotent.
Returns the IDs of the layers created.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:map-write`.

**operationId:** v2.addArtifactsToMap

**path:** /api/v2/gaia/maps/{mapRid}/addArtifactsTo

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

**name:** AddArtifactsToMapRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| artifactGids | listType | False | The GIDs of artifacts to be added to the map. |
| label | stringType | True | The name of the layer to be created |

**example:** {"label":"Example layer"}

### Response

#### Body

The response body to add artifacts to a map, containing the IDs of the created layers.

**name:** AddArtifactsToMapResponse

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| dataLayerIds | listType | False |  |

### Error Responses

| name | description |
| --- | --- |
| ExpectedMapGid | Expected a map Gid. |
| AddArtifactsToMapPermissionDenied | Could not addArtifactsTo the Map. |
