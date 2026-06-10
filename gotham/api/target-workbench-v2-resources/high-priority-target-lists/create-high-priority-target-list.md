---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench-v2-resources/high-priority-target-lists/create-high-priority-target-list/"
title: "Create High Priority Target List \u2022 API Reference"
---
# Create High Priority Target List

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Create a High Priority Target List.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:target-write`.

**operationId:** v2.createHighPriorityTargetList

**path:** /api/v2/targetWorkbench/highPriorityTargetLists

### Operation Type

### Scopes

| name |
| --- |
| api:target-write |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** CreateHighPriorityTargetListRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| targetBoard | stringType | False | The unique identifier for a Target Board |
| targetAois | listType | False |  |
| security | objectType | True | Security settings for board content |
| areaGeo | objectType | False | A Polygon representing the area where this High Priority Target List is applicable. If areaObjectRid exists, that field/area will be used and this field will be ignored. |
| areaObjectRid | stringType | False | The primary key/unique identifier of an object, useful for interacting with Gotham APIs to load and mutate objects. |
| name | stringType | True |  |
| description | stringType | False |  |
| targets | listType | False |  |

**example:** {"targetBoard":"ri.gotham-artifact.0-0.target-board.example","security":{"portionMarkings":["SENSITIVE"],"spaceRid":"ri.compass.main.folder.12345"},"areaGeo":{"points":[{"elevation":0.0,"latitude":0.0,"longitude":0.0}]},"areaObjectRid":"ri.gotham.123-456.object-internal.example","name":"Example target board name.","description":"Example target board description.","targets":[{"targetSubtypes":["Red Car"],"when":"ACQUIRED"}]}

### Response

#### Body

The created HighPriorityTargetList

**name:** HighPriorityTargetList

**example:** {"targetBoard":"ri.gotham-artifact.0-0.target-board.example","security":{"portionMarkings":["SENSITIVE"],"spaceRid":"ri.compass.main.folder.12345"},"areaGeo":{"points":[{"elevation":0.0,"latitude":0.0,"longitude":0.0}]},"areaObjectRid":"ri.gotham.123-456.object-internal.example","name":"Example target board name.","description":"Example target board description.","rid":"ri.gotham-artifact.0-0.hptl.example","targets":[{"targetSubtypes":["Red Car"],"when":"ACQUIRED"}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The unique identifier for a High Priority Target List |
| name | stringType | True |  |
| description | stringType | False |  |
| targetBoard | stringType | False | The unique identifier for a Target Board |
| targets | listType | False |  |
| areaObjectRid | stringType | False | The primary key/unique identifier of an object, useful for interacting with Gotham APIs to load and mutate objects. |
| areaGeo | objectType | False | A Polygon representing the area where this High Priority Target List is applicable. If areaObjectRid exists, that field/area will be used and this field will be ignored. |
| targetAois | listType | False |  |
| security | objectType | True | Security settings for board content |

**example:** {"targetBoard":"ri.gotham-artifact.0-0.target-board.example","security":{"portionMarkings":["SENSITIVE"],"spaceRid":"ri.compass.main.folder.12345"},"areaGeo":{"points":[{"elevation":0.0,"latitude":0.0,"longitude":0.0}]},"areaObjectRid":"ri.gotham.123-456.object-internal.example","name":"Example target board name.","description":"Example target board description.","rid":"ri.gotham-artifact.0-0.hptl.example","targets":[{"targetSubtypes":["Red Car"],"when":"ACQUIRED"}]}

### Error Responses

| name | description |
| --- | --- |
| InvalidClassificationPortionMarkings | The specified portion markings are not valid. |
| InvalidSpaceRid | The space rid is missing or invalid. |
| CreateHighPriorityTargetListPermissionDenied | Could not create the HighPriorityTargetList. |
