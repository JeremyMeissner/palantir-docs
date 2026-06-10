---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench-v2-resources/targets/create-target-intel-target/"
title: "Create Target Intel Target \u2022 API Reference"
---
# Create Target Intel Target

## Endpoint

Create Intel on Target by RID.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:target-write`.

**operationId:** v2.createTargetIntelTarget

**path:** /api/v2/targetWorkbench/targets/{targetRid}/createTargetIntel

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

**name:** CreateTargetIntelTargetRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| id | stringType | True |  |
| name | stringType | True |  |
| description | stringType | False |  |
| domain | enumType | True |  |
| validTime | stringType | True |  |
| location | objectType | False | A circle representing the area a target is located. |
| confidence | numberType | False |  |
| intelType | unionType | True |  |
| source | stringType | False |  |

**example:** {"domain":"SIGINT","confidence":3.0,"name":"Example Intel Name","description":"Intel containing location.","intelType":{"type":"geotimeObservation","geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example"},"validTime":"2023-10-04T14:48:00.000Z","location":{"center":{"elevation":0.0,"latitude":0.0,"longitude":0.0},"radius":1.1},"id":"Example Intel Id","source":"Example source"}

### Response

#### Body

An empty response object indicating the request was successful.

**name:** EmptySuccessResponse

### Error Responses

| name | description |
| --- | --- |
| TargetNotFound | Cannot find target from provided rid. |
| CreateTargetIntelTargetPermissionDenied | Could not createTargetIntel the Target. |
