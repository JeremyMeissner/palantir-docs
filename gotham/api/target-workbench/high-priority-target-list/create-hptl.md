---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench/high-priority-target-list/create-hptl/"
title: "Create a HighPriorityTargetList \u2022 API Reference"
---
# Create a HighPriorityTargetList

## Endpoint

Create a High Priority Target List.
Returns the RID of the created High Priority Target List.

**operationId:** v1.createHptlV2

**path:** /api/gotham/v1/twb/highPriorityTargetList

### Operation Type

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

The request body to create a High Priority Target List

**name:** CreateHighPriorityTargetListRequestV2

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| name | stringType | True |  |
| description | stringType | False |  |
| targetBoard | stringType | False | The unique resource identifier of a Target Board. This is equivalent to a collection RID. |
| targets | listType | False | A list of HighPriorityTargetListTargets |
| areaObjectRid | stringType | False | The primary key/unique identifier of an object, useful for interacting with Gotham APIs to load and mutate objects. |
| areaGeo | objectType | False | A Polygon representing the area where this High Priority Target List is applicable. If areaObjectRid exists, that field will be preferred. |
| targetAois | listType | False |  |
| security | objectType | True | Security mutation details for a target, target board, or hptl. Specifying security overrides the system's default security when creating and updating data. This model may evolve over time for other security features. |

**example:** {"name":"Example hptl name.","description":"Example description.","targetBoard":"ri.gotham-artifact.0-0.target-collection.example","targets":[{"highPriorityTargetListTargetId":"f81d4fae-7dec-11d0-a765-00a0c91e6bf6","targetType":"Airplane","priority":1,"subPriority":4,"category":"Transport","when":"PLANNED","agm":{"2a46fbf6-ff93-4710-951a-015ed5c92441":{"agmId":"2a46fbf6-ff93-4710-951a-015ed5c92441","effectorType":"NEUTRALIZE","effector":"F-16C","effectorPriority":2,"timelinessInMinutes":5}},"aoiId":"123e4567-e89b-12d3-a456-426614174000"},{"highPriorityTargetListTargetId":"54ac3383-b953-4d65-8f98-7c3fbbbb481a","targetType":"Ship","priority":1,"subPriority":2,"category":"Transport","when":"PLANNED","agm":{"2f0df2cb-0737-4675-a481-2c93259a78ae":{"agmId":"2f0df2cb-0737-4675-a481-2c93259a78ae","effectorType":"DESTROY","effector":"M777","effectorPriority":2,"timelinessInMinutes":5}},"aoiId":"123e4567-e89b-12d3-a456-426614174020"}],"areaObjectRid":"ri.gotham-artifact.0-0.object-internal.example","areaGeo":{"points":[{"longitude":1.0,"latitude":1.0,"elevation":1.0}]},"targetAois":[{"id":"123e4567-e89b-12d3-a456-426614174000","name":"Lake215","data":{"type":"entity","entity":"ri.gotham.123-456.object-internal.example"}},{"id":"123e4567-e89b-12d3-a456-426614174020","name":"Lake230","data":{"type":"entity","entity":"ri.gotham.123-456.object-internal.example"}}],"security":{"portionMarkings":["MU"]}}

### Response

#### Body

Success response with the ID of the created High Priority Target List.

**name:** CreateHighPriorityTargetListResponseV2

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| highPriorityTargetListRid | stringType | True |  |
