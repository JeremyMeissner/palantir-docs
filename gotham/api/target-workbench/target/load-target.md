---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench/target/load-target/"
title: "Load a Target \u2022 API Reference"
---
# Load a Target

## Endpoint

Load a Target by RID.

**operationId:** v1.loadTargetV2

**path:** /api/gotham/v1/twb/target/{rid}

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | Target RID |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Response

#### Body

Success response with the requested Target.

**name:** LoadTargetResponseV2

**example:** {"rid":"ri.gotham-artifact.0-0.target.example","name":"Enemy Building","description":"Known enemy building.","targetBoard":"ri.gotham-artifact.0-0.target-collection.example","column":"DRAFT","targetType":"Building","entityRid":"ri.gotham.123-456.object-internal.example","sidc":"SEGPU-------","aimpoints":[{"id":"f81d4fae-7dec-11d0-a765-00a0c91e6bf6","number":1,"name":"Example targetAimPoint name","location":{"center":{"longitude":0.0,"latitude":0.0,"elevation":0.0},"radius":1.1},"geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example","entityRid":"ri.gotham.123-456.object-internal.example"},{"id":"54ac3383-b953-4d65-8f98-7c3fbbbb481a","number":1,"name":"Example targetAimPoint name","location":{"center":{"longitude":0.0,"latitude":0.0,"elevation":0.0},"radius":1.1},"geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example","entityRid":"ri.gotham.123-456.object-internal.example"}],"targetIdentifier":{"customTargetIdentifier":"Example Identifier 000"},"location":{"manualLocation":{"lat":0.0,"lng":0.0,"circularErrorInMeters":0.0,"hae":0.0,"msl":0.0,"agl":0.0}},"highPriorityTargetListTargetSubtype":"Red Car"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| target | objectType | True | The Target object. |
| baseRevisionId | stringType | True | The current version of the Target retrieved. Any modifying operations should be accompanied by this version to avoid concurrent operations made since this version. If there are any conflicting edits that result in changes to these operations when they're applied, that will be noted in the response. |

**example:** {"rid":"ri.gotham-artifact.0-0.target.example","name":"Enemy Building","description":"Known enemy building.","targetBoard":"ri.gotham-artifact.0-0.target-collection.example","column":"DRAFT","targetType":"Building","entityRid":"ri.gotham.123-456.object-internal.example","sidc":"SEGPU-------","aimpoints":[{"id":"f81d4fae-7dec-11d0-a765-00a0c91e6bf6","number":1,"name":"Example targetAimPoint name","location":{"center":{"longitude":0.0,"latitude":0.0,"elevation":0.0},"radius":1.1},"geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example","entityRid":"ri.gotham.123-456.object-internal.example"},{"id":"54ac3383-b953-4d65-8f98-7c3fbbbb481a","number":1,"name":"Example targetAimPoint name","location":{"center":{"longitude":0.0,"latitude":0.0,"elevation":0.0},"radius":1.1},"geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example","entityRid":"ri.gotham.123-456.object-internal.example"}],"targetIdentifier":{"customTargetIdentifier":"Example Identifier 000"},"location":{"manualLocation":{"lat":0.0,"lng":0.0,"circularErrorInMeters":0.0,"hae":0.0,"msl":0.0,"agl":0.0}},"highPriorityTargetListTargetSubtype":"Red Car"}
