---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench-v2-resources/targets/modify-target/"
title: "Modify Target \u2022 API Reference"
---
# Modify Target

## Endpoint

Set current state of Target by RID.

If `sidc` field is specified and invalid according to MIL-STD-2525C specification,
an `InvalidSidc` error is thrown.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:target-write`.

**operationId:** v2.modifyTarget

**path:** /api/v2/targetWorkbench/targets/{targetRid}/modify

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

**name:** ModifyTargetRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| name | stringType | True |  |
| description | stringType | False |  |
| targetType | stringType | False | The resource type of the target. |
| entityRid | stringType | False | The primary key/unique identifier of an object, useful for interacting with Gotham APIs to load and mutate objects. |
| sidc | stringType | False | MIL-STD 2525C Symbol Identification Code. |
| targetIdentifier | objectType | False | Target identifier object for different identifier types. |
| location | objectType | False | An object containing the location source for a target.  This can either be a manual location, a geotimeTrack, and/or a geotrackable entity providing location updates.  The entity, if present, is always the same as the backing entity of the target. |
| highPriorityTargetListTargetSubtype | stringType | False | This subtype will be matched against the subType stored on High Priority Target List Target (HPTLTarget) in order to determine a target's subPriority, in addition to priority and Attack Guidance Matrix (AGM). |
| aimpoints | listType | False |  |
| baseRevisionId | stringType | True | The version of the Target to be modified. The modifying operations will be transformed against any concurrent operations made since this version.  If the supplied version is outdated, the server will respond back with RevisionOutdated exception and the client must resend the request with the updated baseRevisionId. |
| clientId | stringType | False | The client id is used to identify conflicting edits made by the same client, typically due to retries, and discard them. Clients should choose an arbitrary random identifier to distinguish themselves. There is no need persist and re-use the same client id over multiple sessions.  The client id is also used to avoid broadcasting operations to the client who submitted them. |

**example:** {"sidc":"SEGPU-------","entityRid":"ri.gotham.123-456.object-internal.example","highPriorityTargetListTargetSubtype":"Red Car","targetIdentifier":{"customTargetIdentifier":"Example Identifier 000"},"clientId":"123e4567-e89b-12d3-a456-426614174000","aimpoints":[{"entityRid":"ri.gotham.123-456.object-internal.example","geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example","name":"Example targetAimPoint name","location":{"circularErrorInMeters":0.0,"lng":0.0,"msl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"agl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"hae":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"lat":0.0},"id":"f81d4fae-7dec-11d0-a765-00a0c91e6bf6"}],"name":"Example target name.","description":"Example target description.","targetType":"Building","location":{"manualLocation":{"circularErrorInMeters":0.0,"lng":0.0,"msl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"agl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"hae":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"lat":0.0},"geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example","geotrackableEntity":"ri.gotham.123-456.object-internal.example"},"baseRevisionId":1}

### Response

#### Body

An empty response object indicating the request was successful.

**name:** EmptySuccessResponse

### Error Responses

| name | description |
| --- | --- |
| InvalidGeotrackableEntity | The supplied geotrackable entity does not match the backing entity of the target. |
| RevisionOutdated | The provided revision id is behind the current id. |
| ModifyTargetPermissionDenied | Could not modify the Target. |
