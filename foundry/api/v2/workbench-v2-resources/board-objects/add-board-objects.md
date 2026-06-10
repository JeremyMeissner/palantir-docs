---
source_url: "https://www.palantir.com/docs/foundry/api/v2/workbench-v2-resources/board-objects/add-board-objects/"
title: "Add Board Objects"
---
# Add Board Objects

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Adds Foundry Objects to a Workbench Board. This operation links the objects to the board, allowing them to be tracked within the board's workflow. If no state is specified, the objects will be placed in the board's default state (first column). Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:workbench-write. Path parameters. The unique identifier for a Workbench Board. Query parameters. Enables the use of preview functionality. Request body. The RIDs of the Foundry Objects to add to the board. Optional state (column) to place the objects in. If not specified, the objects will be placed in the board's default state (the first state in the board's configured order). Response body. An empty response object indicating the request was successful. Examples. Error responses.
