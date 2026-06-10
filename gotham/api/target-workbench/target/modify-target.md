---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench/target/modify-target/"
title: "Modify a Target \u2022 API Reference"
---
# Modify a Target

## Endpoint

Set current state of Target by RID.

If `sidc` field is specified and invalid according to MIL-STD-2525C specification,
an `InvalidSidc` error is thrown.

**operationId:** v1.modifyTargetV2

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

### Request

#### Body

The request body to modify a Target. The entityRid is the RID of the object being targeted.
If a geotrackableEntity is supplied, it must match the entityRid. Otherwise, 'InvalidGeotrackableEntity' will be
thrown.

**name:** ModifyTargetRequestV2

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| name | stringType | True |  |
| description | stringType | False |  |
| targetType | stringType | False | The resource type of the target. Example: Building |
| entityRid | stringType | False | The primary key/unique identifier of an object, useful for interacting with Gotham APIs to load and mutate objects. |
| sidc | stringType | False | MIL-STD 2525C Symbol Identification Code |
| targetIdentifier | objectType | False | Target identifier object for different identifier types |
| location | objectType | False | An object containing the location source for a target.  This can either be a manual location, a geotimeTrack, and/or a geotrackable entity providing location updates.  The entity, if present, is always the same as the backing entity of the target. |
| highPriorityTargetListTargetSubtype | stringType | False | This subtype will be matched against the subType stored on HptlTarget in order to determine a target's subPriority, as well as priority in addition to priority and AGM. |
| aimpoints | listType | False |  |
| baseRevisionId | stringType | True | The version of the Target to be modified. The modifying operations will be transformed against any concurrent operations made since this version.   If the supplied version is outdated, the server will respond back with RevisionTooOld exception and the client must resend the request with the updated baseRevisionId. |
| clientId | stringType | False | The client id is used to identify conflicting edits made by the same client, typically due to retries, and discard them. Clients should choose an arbitrary random identifier to distinguish themselves. There is no need persist and re-use the same client id over multiple sessions.  The client id is also used to avoid broadcasting operations to the client who submitted them. |

**example:** {"name":"Enemy Building","description":"Known enemy building.","targetType":"Building","entityRid":"ri.gotham.123-456.object-internal.example","sidc":"SEGPU-------","aimpoints":[{"id":"f81d4fae-7dec-11d0-a765-00a0c91e6bf6","number":1,"name":"Example targetAimPoint name","location":{"center":{"longitude":4.0,"latitude":4.0,"elevation":4.0},"radius":1.1},"geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example","entityRid":"ri.gotham.123-456.object-internal.example"},{"id":"54ac3383-b953-4d65-8f98-7c3fbbbb481a","number":1,"name":"Example targetAimPoint name","location":{"center":{"longitude":0.0,"latitude":0.0,"elevation":0.0},"radius":1.1},"geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example","entityRid":"ri.gotham.123-456.object-internal.example"}],"targetIdentifier":{"customTargetIdentifier":"Example Identifier 005"},"location":{"manualLocation":{"lat":0.0,"lng":0.0,"circularErrorInMeters":0.0,"hae":0.0,"msl":0.0,"agl":0.0}},"highPriorityTargetListTargetSubtype":"Blue Car","clientId":"123e4567-e89b-12d3-a456-426614174000","baseRevisionId":1}

### Response

#### Body

Success response.

**name:** EmptySuccessResponse
