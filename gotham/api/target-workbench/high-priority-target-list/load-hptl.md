---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench/high-priority-target-list/load-hptl/"
title: "Load a HighPriorityTargetList \u2022 API Reference"
---
# Load a HighPriorityTargetList

## Endpoint

Load a High Priority Target List by RID.

**operationId:** v1.loadHptlV2

**path:** /api/gotham/v1/twb/highPriorityTargetList/{rid}

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | High Priority Target List RID |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Response

#### Body

Success response with the requested High Priority Target List.

**name:** LoadHighPriorityTargetListResponseV2

**example:** {"rid":"ri.gotham-artifact.0-0.hptl.example","description":"Example description.","targets":[{"highPriorityTargetListTargetId":"f81d4fae-7dec-11d0-a765-00a0c91e6bf6","targetType":"Airplane","priority":1,"subPriority":4,"category":"Transport","when":"PLANNED","agm":{"2a46fbf6-ff93-4710-951a-015ed5c92441":{"agmId":"2a46fbf6-ff93-4710-951a-015ed5c92441","effectorType":"NEUTRALIZE","effector":"F-16C","effectorPriority":2,"timelinessInMinutes":5}},"aoiId":"123e4567-e89b-12d3-a456-426614174000"},{"highPriorityTargetListTargetId":"54ac3383-b953-4d65-8f98-7c3fbbbb481a","targetType":"Ship","priority":1,"subPriority":2,"category":"Transport","when":"PLANNED","agm":{"2f0df2cb-0737-4675-a481-2c93259a78ae":{"agmId":"2f0df2cb-0737-4675-a481-2c93259a78ae","effectorType":"DESTROY","effector":"M777","effectorPriority":2,"timelinessInMinutes":5}},"aoiId":"123e4567-e89b-12d3-a456-426614174020"}],"areaObjectRid":"ri.gotham-artifact.0-0.object-internal.example","areaGeo":{"points":[{"longitude":1.0,"latitude":1.0,"elevation":1.0}]},"targetAois":[{"id":"123e4567-e89b-12d3-a456-426614174000","name":"Lake215","data":{"type":"entity","entity":"ri.gotham.123-456.object-internal.example"}},{"id":"123e4567-e89b-12d3-a456-426614174020","name":"Lake230","data":{"type":"entity","entity":"ri.gotham.123-456.object-internal.example"}}],"baseRevisionId":1}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| highPriorityTargetList | objectType | True | The High Priority Target List object. |
| baseRevisionId | integerType | True | The current version of the HighPriorityTargetList retrieved. Any modifying operations should be accompanied by this version to avoid concurrent operations made since this version. If there are any conflicting edits that result in changes to these operations when they're applied, that will be noted in the response. |

**example:** {"rid":"ri.gotham-artifact.0-0.hptl.example","description":"Example description.","targets":[{"highPriorityTargetListTargetId":"f81d4fae-7dec-11d0-a765-00a0c91e6bf6","targetType":"Airplane","priority":1,"subPriority":4,"category":"Transport","when":"PLANNED","agm":{"2a46fbf6-ff93-4710-951a-015ed5c92441":{"agmId":"2a46fbf6-ff93-4710-951a-015ed5c92441","effectorType":"NEUTRALIZE","effector":"F-16C","effectorPriority":2,"timelinessInMinutes":5}},"aoiId":"123e4567-e89b-12d3-a456-426614174000"},{"highPriorityTargetListTargetId":"54ac3383-b953-4d65-8f98-7c3fbbbb481a","targetType":"Ship","priority":1,"subPriority":2,"category":"Transport","when":"PLANNED","agm":{"2f0df2cb-0737-4675-a481-2c93259a78ae":{"agmId":"2f0df2cb-0737-4675-a481-2c93259a78ae","effectorType":"DESTROY","effector":"M777","effectorPriority":2,"timelinessInMinutes":5}},"aoiId":"123e4567-e89b-12d3-a456-426614174020"}],"areaObjectRid":"ri.gotham-artifact.0-0.object-internal.example","areaGeo":{"points":[{"longitude":1.0,"latitude":1.0,"elevation":1.0}]},"targetAois":[{"id":"123e4567-e89b-12d3-a456-426614174000","name":"Lake215","data":{"type":"entity","entity":"ri.gotham.123-456.object-internal.example"}},{"id":"123e4567-e89b-12d3-a456-426614174020","name":"Lake230","data":{"type":"entity","entity":"ri.gotham.123-456.object-internal.example"}}],"baseRevisionId":1}
