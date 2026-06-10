---
source_url: "https://www.palantir.com/docs/gotham/api/v2/target-workbench-v2-resources/target-boards/create-target-board/"
parquet_url: "/gotham/api/v2/target-workbench-v2-resources/target-boards/create-target-board/"
title: "Create Target Board"
fetched_at: "2026-05-12T19:34:35.779Z"
---
Create Target Board. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. By default, create a TargetBoard with default columns: IDENTIFIED TARGET, PRIORITIZED TARGET, IN COORDINATION, IN EXECUTION, COMPLETE. Returns the RID of the created TargetBoard. The security.spaceRid field defaults to your user's space if there is only one. Use the List Spaces endpoint at /api/v2/filesystem/spaces to get the spaces your user has access to. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:target-write. Query parameters. Enables the use of preview functionality. Request body. Security settings for the board. Configuration for a target board. Response body. The created TargetBoard. The unique identifier for a Target Board. Configuration for a target board. Security settings for the board. Examples. Error responses.
