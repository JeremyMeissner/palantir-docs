---
source_url: "https://www.palantir.com/docs/gotham/api/map-rendering-v2-resources/invocation-objects/render-invocation-object/"
title: "Render Invocation Object \u2022 API Reference"
---
# Render Invocation Object

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:map-read`.

**operationId:** v2.renderInvocationObject

**path:** /api/v2/mapRendering/invocationObject/render

### Operation Type

### Scopes

| name |
| --- |
| api:map-read |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** RenderInvocationObjectRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| capabilities | objectType | True | The render capability of the client. Renderables will be returned in the best possible format that's supported by the client. |
| invocations | listType | False |  |

**example:** {"capabilities":{"supportedRenderableContent":["GEOMETRY"]},"invocations":[{"id":"InvocationOne","sourcingOnly":false,"objects":{"type":"objectSet","objectSetRid":"ri.object-set.main.versioned-object-set.51060b6a-42de-4a2c-8a03-cc5e80a1b610"},"renderer":{"type":"standard","get":{}}}]}

### Response

#### Body

**name:** RenderObjectsResponse

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| renderables | listType | False |  |
| sourcings | listType | False |  |

### Error Responses

| name | description |
| --- | --- |
| RenderInvocationObjectPermissionDenied | Could not render the InvocationObject. |
