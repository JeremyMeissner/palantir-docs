---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench-v2-resources/targets/create-target/"
title: "Create Target \u2022 API Reference"
---
# Create Target

## Endpoint

Create a Target.
Returns the RID of the created Target.

If `sidc` field is specified and invalid according to MIL-STD-2525C specification,
an `InvalidSidc` error is thrown.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:target-write`.

**operationId:** v2.createTarget

**path:** /api/v2/targetWorkbench/targets

### Operation Type

### Scopes

| name |
| --- |
| api:target-write |

### Request

#### Body

**name:** CreateTargetRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| sidc | stringType | False | MIL-STD 2525C Symbol Identification Code. |
| highPriorityTargetListTargetSubtype | stringType | False | This subtype will be matched against the subType stored on High Priority Target List Target (HPTLTarget) in order to determine a target's subPriority, in addition to priority and Attack Guidance Matrix (AGM). |
| column | stringType | True | Equivalent to a collection column ID. The ID of a TargetCollectionColumn, default values are: DRAFT (Identified target), PLAN_DEVELOPMENT (Prioritized target), PLANNED (In coordination), EXECUTION (In execution), CLOSED (Complete). |
| description | stringType | False |  |
| targetType | stringType | False | The resource type of the target. |
| targetBoard | stringType | True | The unique identifier for a Target Board |
| entityRid | stringType | False | The primary key/unique identifier of an object, useful for interacting with Gotham APIs to load and mutate objects. |
| targetIdentifier | objectType | False | Target identifier object for different identifier types. |
| security | objectType | True | Security settings for board content |
| aimpoints | listType | False |  |
| detectionReasoning | objectType | False |  |
| name | stringType | True |  |
| location | objectType | False | An object containing the location source for a target.  This can either be a manual location, a geotimeTrack, and/or a geotrackable entity providing location updates.  The entity, if present, is always the same as the backing entity of the target. |

**example:** {"sidc":"SEGPU-------","highPriorityTargetListTargetSubtype":"Red Car","column":"DRAFT","description":"Example target description.","targetType":"Building","targetBoard":"ri.gotham-artifact.0-0.target-board.example","entityRid":"ri.gotham.123-456.object-internal.example","targetIdentifier":{"customTargetIdentifier":"Example Identifier 000"},"security":{"portionMarkings":["SENSITIVE"],"spaceRid":"ri.compass.main.folder.12345"},"aimpoints":[{"entityRid":"ri.gotham.123-456.object-internal.example","geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example","name":"Example targetAimPoint name","location":{"circularErrorInMeters":0.0,"lng":0.0,"msl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"agl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"hae":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"lat":0.0},"id":"f81d4fae-7dec-11d0-a765-00a0c91e6bf6"}],"detectionReasoning":{"detectionType":"AI_AUTO_DETECTION","aiReasoning":{"systemPrompt":"Identify potential targets in the area.","debugLogs":"Debug log example","model":"LLM Model v1.0","taskPrompt":"Analyze satellite images for unusual activity."},"reasoning":"The target was identified based on unusual heat signatures detected in the area.","agentVersion":"1.2.3","location":{"circularErrorInMeters":0.0,"lng":0.0,"msl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"agl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"hae":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"lat":0.0},"algorithmName":"Example Algorithm","timestamp":"2025-04-11T10:00:00Z"},"name":"Example target name.","location":{"manualLocation":{"circularErrorInMeters":0.0,"lng":0.0,"msl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"agl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"hae":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"lat":0.0},"geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example","geotrackableEntity":"ri.gotham.123-456.object-internal.example"}}

### Response

#### Body

The created Target

**name:** Target

**example:** {"sidc":"SEGPU-------","highPriorityTargetListTargetSubtype":"Red Car","column":"DRAFT","description":"Example target description.","targetType":"Building","rid":"ri.gotham-artifact.0-0.target.example","targetBoard":"ri.gotham-artifact.0-0.target-board.example","entityRid":"ri.gotham.123-456.object-internal.example","targetIdentifier":{"customTargetIdentifier":"Example Identifier 000"},"security":{"portionMarkings":["SENSITIVE"],"spaceRid":"ri.compass.main.folder.12345"},"aimpoints":[{"entityRid":"ri.gotham.123-456.object-internal.example","geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example","name":"Example targetAimPoint name","location":{"circularErrorInMeters":0.0,"lng":0.0,"msl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"agl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"hae":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"lat":0.0},"id":"f81d4fae-7dec-11d0-a765-00a0c91e6bf6"}],"detectionReasoning":{"detectionType":"AI_AUTO_DETECTION","aiReasoning":{"systemPrompt":"Identify potential targets in the area.","debugLogs":"Debug log example","model":"LLM Model v1.0","taskPrompt":"Analyze satellite images for unusual activity."},"reasoning":"The target was identified based on unusual heat signatures detected in the area.","agentVersion":"1.2.3","location":{"circularErrorInMeters":0.0,"lng":0.0,"msl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"agl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"hae":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"lat":0.0},"algorithmName":"Example Algorithm","timestamp":"2025-04-11T10:00:00Z"},"name":"Example target name.","location":{"manualLocation":{"circularErrorInMeters":0.0,"lng":0.0,"msl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"agl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"hae":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"lat":0.0},"geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example","geotrackableEntity":"ri.gotham.123-456.object-internal.example"}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The unique identifier for a Target |
| name | stringType | True |  |
| description | stringType | False |  |
| targetBoard | stringType | True | The unique identifier for a Target Board |
| column | stringType | True | Equivalent to a collection column ID. The ID of a TargetCollectionColumn, default values are: DRAFT (Identified target), PLAN_DEVELOPMENT (Prioritized target), PLANNED (In coordination), EXECUTION (In execution), CLOSED (Complete). |
| targetType | stringType | False | The resource type of the target. |
| entityRid | stringType | False | The primary key/unique identifier of an object, useful for interacting with Gotham APIs to load and mutate objects. |
| sidc | stringType | False | MIL-STD 2525C Symbol Identification Code. |
| targetIdentifier | objectType | False | Target identifier object for different identifier types. |
| location | objectType | False | An object containing the location source for a target.  This can either be a manual location, a geotimeTrack, and/or a geotrackable entity providing location updates.  The entity, if present, is always the same as the backing entity of the target. |
| highPriorityTargetListTargetSubtype | stringType | False | This subtype will be matched against the subType stored on High Priority Target List Target (HPTLTarget) in order to determine a target's subPriority, in addition to priority and Attack Guidance Matrix (AGM). |
| aimpoints | listType | False |  |
| security | objectType | True | Security settings for board content |
| detectionReasoning | objectType | False |  |

**example:** {"sidc":"SEGPU-------","highPriorityTargetListTargetSubtype":"Red Car","column":"DRAFT","description":"Example target description.","targetType":"Building","rid":"ri.gotham-artifact.0-0.target.example","targetBoard":"ri.gotham-artifact.0-0.target-board.example","entityRid":"ri.gotham.123-456.object-internal.example","targetIdentifier":{"customTargetIdentifier":"Example Identifier 000"},"security":{"portionMarkings":["SENSITIVE"],"spaceRid":"ri.compass.main.folder.12345"},"aimpoints":[{"entityRid":"ri.gotham.123-456.object-internal.example","geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example","name":"Example targetAimPoint name","location":{"circularErrorInMeters":0.0,"lng":0.0,"msl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"agl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"hae":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"lat":0.0},"id":"f81d4fae-7dec-11d0-a765-00a0c91e6bf6"}],"detectionReasoning":{"detectionType":"AI_AUTO_DETECTION","aiReasoning":{"systemPrompt":"Identify potential targets in the area.","debugLogs":"Debug log example","model":"LLM Model v1.0","taskPrompt":"Analyze satellite images for unusual activity."},"reasoning":"The target was identified based on unusual heat signatures detected in the area.","agentVersion":"1.2.3","location":{"circularErrorInMeters":0.0,"lng":0.0,"msl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"agl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"hae":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"lat":0.0},"algorithmName":"Example Algorithm","timestamp":"2025-04-11T10:00:00Z"},"name":"Example target name.","location":{"manualLocation":{"circularErrorInMeters":0.0,"lng":0.0,"msl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"agl":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"hae":{"elevationInMeters":0.0,"linearErrorInMeters":0.0},"lat":0.0},"geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example","geotrackableEntity":"ri.gotham.123-456.object-internal.example"}}

### Error Responses

| name | description |
| --- | --- |
| InvalidGeotrackableEntity | The supplied geotrackable entity does not match the backing entity of the target. |
| InvalidSidc | The specified symbol identification code (SIDC) was not valid based on MIL-STD-2525C specification. |
| InvalidSpaceRid | The space rid is missing or invalid. |
| CreateTargetPermissionDenied | Could not create the Target. |
