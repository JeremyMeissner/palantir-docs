---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench-v2-resources/high-priority-target-lists/load-high-priority-target-list/"
title: "Load High Priority Target List \u2022 API Reference"
---
# Load High Priority Target List

## Endpoint

Load a High Priority Target List by RID.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:target-read`.

**operationId:** v2.loadHighPriorityTargetList

**path:** /api/v2/targetWorkbench/highPriorityTargetLists/{highPriorityTargetListRid}/load

### Operation Type

### Scopes

| name |
| --- |
| api:target-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| highPriorityTargetListRid | stringType | True | The unique identifier for a High Priority Target List |

### Response

#### Body

Success response with the requested Target Board.

**name:** LoadHighPriorityTargetListResponse

**example:** {"highPriorityTargetList":{"areaGeo":{"points":[{"elevation":0.0,"latitude":0.0,"longitude":0.0}]},"areaObjectId":"ri.gotham.123-456.object-internal.example","rid":"ri.gotham-artifact.0-0.hptl.example","targets":[{"targetSubtypes":["Red Car"],"when":"ACQUIRED"}]},"baseRevisionId":1}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| highPriorityTargetList | objectType | True | The High Priority Target List object. |
| baseRevisionId | integerType | True | The current version of the retrieved HighPriorityTargetList. Any modifying operations should be accompanied by this version to avoid concurrent operations made since this version. If there are any conflicting edits that result in changes to these operations when they are applied, it will be noted in the response. |

**example:** {"highPriorityTargetList":{"areaGeo":{"points":[{"elevation":0.0,"latitude":0.0,"longitude":0.0}]},"areaObjectId":"ri.gotham.123-456.object-internal.example","rid":"ri.gotham-artifact.0-0.hptl.example","targets":[{"targetSubtypes":["Red Car"],"when":"ACQUIRED"}]},"baseRevisionId":1}

### Error Responses

| name | description |
| --- | --- |
| HighPriorityTargetListNotFound | Cannot find High Priority Target List from provided RID |
| LoadHighPriorityTargetListPermissionDenied | Could not load the HighPriorityTargetList. |
