---
source_url: "https://www.palantir.com/docs/foundry/api/v2/workbench-v2-resources/board-objects/move-board-objects/"
title: "Move Board Objects"
---
# Move Board Objects

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Moves Foundry Objects from their current state to a different state on a Workbench Board. This operation preserves the objects' board item identifiers and edit history, allowing users to track the objects' progression through workflow states. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:workbench-write. Path parameters. The unique identifier for a Workbench Board. Query parameters. Enables the use of preview functionality. Request body. The RIDs of the Foundry Objects to move. The destination state (column) to move the objects to. Response body. An empty response object indicating the request was successful. Examples. Error responses.
