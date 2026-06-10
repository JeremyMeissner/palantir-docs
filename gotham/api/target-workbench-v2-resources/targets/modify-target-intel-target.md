---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench-v2-resources/targets/modify-target-intel-target/"
title: "Modify Target Intel Target \u2022 API Reference"
---
# Modify Target Intel Target

## Endpoint

Modify Intel on Target by RID and IntelId.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:target-write`.

**operationId:** v2.modifyTargetIntelTarget

**path:** /api/v2/targetWorkbench/targets/{targetRid}/modifyTargetIntel

### Operation Type

### Scopes

| name |
| --- |
| api:target-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| targetRid | stringType | True | The unique identifier for a Target |

### Request

#### Body

**name:** ModifyTargetIntelTargetRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| intel | listType | False |  |

**example:** {"intel":[{"domain":"SIGINT","confidence":3.0,"name":"Example Intel Name","description":"Intel containing location.","intelType":{"type":"geotimeObservation","geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example"},"validTime":"2023-10-04T14:48:00.000Z","location":{"center":{"elevation":0.0,"latitude":0.0,"longitude":0.0},"radius":1.1},"id":"Example Intel Id"}]}

### Response

#### Body

The response body returned when modifying intel attached to a target.

**name:** ModifyTargetIntelResponse

**example:** {"updatedIntelIds":["Example Intel Id"]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| updatedIntelIds | listType | False |  |

**example:** {"updatedIntelIds":["Example Intel Id"]}

### Error Responses

| name | description |
| --- | --- |
| TargetNotFound | Cannot find target from provided rid. |
| ModifyTargetIntelTargetPermissionDenied | Could not modifyTargetIntel the Target. |
