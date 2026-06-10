---
source_url: "https://www.palantir.com/docs/gotham/api/v2/target-workbench-v2-resources/high-priority-target-lists/load-high-priority-target-list/"
title: "Load High Priority Target List"
---
# Load High Priority Target List

Load a High Priority Target List by RID. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:target-read. Path parameters. The unique identifier for a High Priority Target List. Response body. Success response with the requested Target Board. The High Priority Target List object. The current version of the retrieved HighPriorityTargetList. Any modifying operations should be accompanied by this version to avoid concurrent operations made since this version. If there are any conflicting edits that result in changes to these operations when they are applied, it will be noted in the response. Examples. Error responses.
