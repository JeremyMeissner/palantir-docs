---
source_url: "https://www.palantir.com/docs/gotham/api/v1/target-workbench/high-priority-target-list/create-hptl/"
title: "Create a HighPriorityTargetList"
---
# Create a HighPriorityTargetList

Create a High Priority Target List. Returns the RID of the created High Priority Target List. Query parameters. Represents a boolean value that restricts an endpoint to preview mode when set to true. Request body. The request body to create a High Priority Target List. The unique resource identifier of a Target Board. This is equivalent to a collection RID. A list of HighPriorityTargetListTargets. The primary key/unique identifier of an object, useful for interacting with Gotham APIs to load and mutate objects. A Polygon representing the area where this High Priority Target List is applicable. If areaObjectRid exists, that field will be preferred. Security mutation details for a target, target board, or hptl. Specifying security overrides the system's default security when creating and updating data. This model may evolve over time for other security features. Response body. Success response with the ID of the created High Priority Target List. Examples.
