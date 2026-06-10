---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench-v2-resources/targets/load-target/"
title: "Load Target \u2022 API Reference"
---
# Load Target

## Endpoint

Load Target by RID.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:target-read`.

**operationId:** v2.loadTarget

**path:** /api/v2/targetWorkbench/targets/{targetRid}/load

### Operation Type

### Scopes

| name |
| --- |
| api:target-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| targetRid | stringType | True | The unique identifier for a Target |

### Response

#### Body

Success response with the requested Target. The objectRid is the RID of the object being targeted.

**name:** LoadTargetResponse

**example:** {"baseRevisionId":1,"target":{"sidc":"SEGPU-------","entityRid":"ri.gotham.123-456.object-internal.example","highPriorityTargetListTargetSubtype":"Red Car","targetIdentifier":{"customTargetIdentifier":"Example Identifier 000"},"aimpoints":[{"entityRid":"ri.gotham.123-456.object-internal.example","geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example","name":"Example targetAimPoint name","location":{"circularErrorInMeters":0.0,"lng":0.0,"msl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"agl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"hae":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"lat":0.0},"id":"f81d4fae-7dec-11d0-a765-00a0c91e6bf6"}],"name":"Example target name.","description":"Example target description.","targetBoards":["ri.gotham-artifact.0-0.target-board.example"],"targetType":"Building","location":{"manualLocation":{"circularErrorInMeters":0.0,"lng":0.0,"msl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"agl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"hae":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"lat":0.0},"geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example","geotrackableEntity":"ri.gotham.123-456.object-internal.example"},"rid":"ri.gotham-artifact.0-0.target.example","intel":[{"domain":"SIGINT","confidence":3.0,"name":"Example Intel Name","description":"Intel containing location.","intelType":{"type":"geotimeObservation","geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example"},"validTime":"2023-10-04T14:48:00.000Z","location":{"center":{"elevation":0.0,"latitude":0.0,"longitude":0.0},"radius":1.1},"id":"Example Intel Id"}]}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| target | objectType | True |  |
| baseRevisionId | stringType | True | The current version of the Target retrieved. Any modifying operations should be accompanied by this version to avoid concurrent operations made since this version. If there are any conflicting edits that result in changes to these operations when they're applied, that will be noted in the response. |

**example:** {"baseRevisionId":1,"target":{"sidc":"SEGPU-------","entityRid":"ri.gotham.123-456.object-internal.example","highPriorityTargetListTargetSubtype":"Red Car","targetIdentifier":{"customTargetIdentifier":"Example Identifier 000"},"aimpoints":[{"entityRid":"ri.gotham.123-456.object-internal.example","geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example","name":"Example targetAimPoint name","location":{"circularErrorInMeters":0.0,"lng":0.0,"msl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"agl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"hae":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"lat":0.0},"id":"f81d4fae-7dec-11d0-a765-00a0c91e6bf6"}],"name":"Example target name.","description":"Example target description.","targetBoards":["ri.gotham-artifact.0-0.target-board.example"],"targetType":"Building","location":{"manualLocation":{"circularErrorInMeters":0.0,"lng":0.0,"msl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"agl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"hae":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"lat":0.0},"geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example","geotrackableEntity":"ri.gotham.123-456.object-internal.example"},"rid":"ri.gotham-artifact.0-0.target.example","intel":[{"domain":"SIGINT","confidence":3.0,"name":"Example Intel Name","description":"Intel containing location.","intelType":{"type":"geotimeObservation","geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example"},"validTime":"2023-10-04T14:48:00.000Z","location":{"center":{"elevation":0.0,"latitude":0.0,"longitude":0.0},"radius":1.1},"id":"Example Intel Id"}]}}

### Error Responses

| name | description |
| --- | --- |
| TargetNotFound | Cannot find target from provided rid. |
| LoadTargetPermissionDenied | Could not load the Target. |
