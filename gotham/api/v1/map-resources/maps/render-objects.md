---
source_url: "https://www.palantir.com/docs/gotham/api/v1/map-resources/maps/render-objects/"
title: "Rendering Foundry Objects"
---
# Rendering Foundry Objects

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Stateless api to fetch a snapshot of renderables for a given object set. Only includes initial renderable values in snapshot, does not reflect changes made while rendering. Query parameters. Represents a boolean value that restricts an endpoint to preview mode when set to true. Request body. Request to render Foundry objects. A request is considered as a single session, thus the invocations included should have unique invocation IDs. The render capability of the client. Renderables will be returned in the best possible format that's supported by the client. Response body. A successful load layers response. Examples.
