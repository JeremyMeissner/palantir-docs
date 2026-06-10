---
source_url: "https://www.palantir.com/docs/gotham/api/v1/target-workbench/high-priority-target-list/modify-hptl/"
title: "Modify a HighPriorityTargetList"
---
# Modify a HighPriorityTargetList

Modify a High Priority Target List by RID. Path parameters. High Priority Target List RID. Query parameters. Represents a boolean value that restricts an endpoint to preview mode when set to true. Request body. The request body to modify a High Priority Target List from a R. The unique resource identifier of a Target Board. This is equivalent to a collection RID. A list of HighPriorityTargetListTargets. The primary key/unique identifier of an object, useful for interacting with Gotham APIs to load and mutate objects. A Polygon representing the area where this High Priority Target List is applicable. If areaObjectRid exists, that field will be preferred. The current version of the HighPriorityTargetList to be modified. Any modifying operations should be accompanied by this version to avoid concurrent operations made since this version. If there are any conflicting edits that result in changes to these operations when they're applied, that will be noted in the response. Response body. Success response. Examples.
