---
source_url: "https://www.palantir.com/docs/gotham/api/map-resources/maps/render-objects/"
title: "Rendering Foundry Objects \u2022 API Reference"
---
# Rendering Foundry Objects

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Stateless api to fetch a snapshot of renderables for a given object set. Only includes initial renderable values
in snapshot, does not reflect changes made while rendering.

**operationId:** v1.renderObjects

**path:** /api/gotham/v1/maprendering/render

### Operation Type

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

Request to render Foundry objects. A request is considered as a single session, thus the invocations included
should have unique invocation IDs.

**name:** RenderObjectsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| capabilities | objectType | True | The render capability of the client. Renderables will be returned in the best possible format that's supported by the client. |
| invocations | listType | False |  |

**example:** {"capabilities":{"supportedRenderableContent":["GEOMETRY"]},"invocations":[{"id":"InvocationOne","sourcingOnly":false,"objects":{"type":"objectSet","objectSetRid":"ri.object-set.main.object-set.5958b23c-88f7-4f0e-a844-c3027f93705d"},"renderer":{"type":"standard"}},{"id":"InvocationTwo","objects":{"type":"objectSet","objectSetRid":"ri.object-set.main.object-set.6bdee6b7-c501-47bc-8e34-dba162dfa505"},"renderer":{"type":"standard"}}]}

### Response

#### Body

A successful load layers response.

**name:** RenderObjectsResponse

**example:** {"renderables":[{"id":"6BwZj7AL19-cQDMlpgQy2SPudRbTCjKQ2IHxKIQK8V8","invocation":"InvocationOne","sourcing":"vXYotEA3rVgfK2otPbQsDD4RM_WudkatTqOoiJuLqJM","content":{"":{"type":"geometry","geometry":{"type":"Point","coordinates":[-78.63919,35.78043]},"style":{"symbolStyle":{"symbol":{"type":"generic","id":"ePkllYLiI7HHUFwC7Gyk5haAZvwB3ioZ3w"},"size":8,"opacity":255}}}}}],"sourcings":[{"id":"vXYotEA3rVgfK2otPbQsDD4RM_WudkatTqOoiJuLqJM","content":{"type":"object","objectType":"ri.ontology.main.object-type.dd1d04a7-10ee-429c-b0a6-69b3302633af","primaryKey":{"ri.ontology.main.property.774274be-7074-4e61-b9ac-88a5d268b4f3":"3d0b48c8-3748-4f52-b6da-5d049a31be15"}}}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| renderables | listType | False |  |
| sourcings | listType | False |  |

**example:** {"renderables":[{"id":"6BwZj7AL19-cQDMlpgQy2SPudRbTCjKQ2IHxKIQK8V8","invocation":"InvocationOne","sourcing":"vXYotEA3rVgfK2otPbQsDD4RM_WudkatTqOoiJuLqJM","content":{"":{"type":"geometry","geometry":{"type":"Point","coordinates":[-78.63919,35.78043]},"style":{"symbolStyle":{"symbol":{"type":"generic","id":"ePkllYLiI7HHUFwC7Gyk5haAZvwB3ioZ3w"},"size":8,"opacity":255}}}}}],"sourcings":[{"id":"vXYotEA3rVgfK2otPbQsDD4RM_WudkatTqOoiJuLqJM","content":{"type":"object","objectType":"ri.ontology.main.object-type.dd1d04a7-10ee-429c-b0a6-69b3302633af","primaryKey":{"ri.ontology.main.property.774274be-7074-4e61-b9ac-88a5d268b4f3":"3d0b48c8-3748-4f52-b6da-5d049a31be15"}}}]}
