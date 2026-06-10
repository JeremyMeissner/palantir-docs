---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench/"
title: "Create a Target \u2022 API Reference"
---
# Create a Target

## Endpoint

Create a Target.
Returns the RID of the created Target.

If `sidc` field is specified and invalid according to MIL-STD-2525C specification,
an `InvalidSidc` error is thrown.

**operationId:** v1.createTargetV2

**path:** /api/gotham/v1/twb/target

### Operation Type

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

The request body to create a Target. The entityRid is the RID of the object being targeted. 
If a geotrackableEntity is supplied, it must match the entityRid. Otherwise, 'InvalidGeotrackableEntity' will be
thrown.

**name:** CreateTargetRequestV2

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| name | stringType | True |  |
| description | stringType | False |  |
| targetBoard | stringType | True | The unique resource identifier of a Target Board. This is equivalent to a collection RID. |
| column | stringType | True | Equivalent to a collection column ID. The ID of a TargetCollectionColumn, default values are: DRAFT (Identified target), PLAN_DEVELOPMENT (Prioritized target), PLANNED (In coordination), EXECUTION (In execution), CLOSED (Complete). |
| targetType | stringType | False | The resource type of the target. Example: Building |
| entityRid | stringType | False | The primary key/unique identifier of an object, useful for interacting with Gotham APIs to load and mutate objects. |
| entityObjectReference | objectType | False | A reference to an entity using object type api name and primary key. |
| sidc | stringType | False | MIL-STD 2525C Symbol Identification Code |
| targetIdentifier | objectType | False | Target identifier object for different identifier types |
| location | objectType | False | An object containing the location source for a target.  This can either be a manual location, a geotimeTrack, and/or a geotrackable entity providing location updates.  The entity, if present, is always the same as the backing entity of the target. |
| highPriorityTargetListTargetSubtype | stringType | False | This subtype will be matched against the subType stored on HptlTarget in order to determine a target's subPriority, as well as priority in addition to priority and AGM. |
| aimpoints | listType | False |  |
| security | objectType | True | Security mutation details for a target, target board, or hptl. Specifying security overrides the system's default security when creating and updating data. This model may evolve over time for other security features. |
| detectionReasoning | objectType | False |  |

**example:** {"name":"Enemy Building","description":"Known enemy building.","targetBoard":"ri.gotham-artifact.0-0.target-board.example","column":"DRAFT","targetType":"Building","entityRid":"ri.gotham.123-456.object-internal.example","sidc":"SEGPU-------","aimpoints":[{"id":"f81d4fae-7dec-11d0-a765-00a0c91e6bf6","number":1,"name":"Example targetAimPoint name","location":{"center":{"longitude":0.0,"latitude":0.0,"elevation":0.0},"radius":1.1},"geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example","entityRid":"ri.gotham.123-456.object-internal.example"},{"id":"54ac3383-b953-4d65-8f98-7c3fbbbb481a","number":1,"name":"Example targetAimPoint name","location":{"center":{"longitude":0.0,"latitude":0.0,"elevation":0.0},"radius":1.1},"geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example","entityRid":"ri.gotham.123-456.object-internal.example"}],"targetIdentifier":{"customTargetIdentifier":"Example Identifier 000"},"location":{"manualLocation":{"lat":0.0,"lng":0.0,"circularErrorInMeters":0.0,"hae":0.0,"msl":0.0,"agl":0.0},"geotrackableEntity":"ri.gotham.123-456.object-internal.example"},"highPriorityTargetListTargetSubtype":"Red Car","security":{"portionMarkings":["SENSITIVE"]},"detectionReasoning":{"algorithmName":"Example Algorithm","aiReasoning":{"debugLogs":"Debug log example","model":"LLM Model v1.0","systemPrompt":"Identify potential targets in the area.","taskPrompt":"Analyze satellite images for unusual activity."},"configurationObjectRid":"ri.foundry.0-0.config-object.example","detectionType":"AI_AUTO_DETECTION","location":{"center":{"longitude":0.0,"latitude":0.0,"elevation":0.0},"radius":1.1},"reasoning":"The target was identified based on unusual heat signatures detected in the area.","timestamp":"2025-04-11T10:00:00Z","agentVersion":"1.2.3"}}

### Response

#### Body

Success response with the RID of the created target.

**name:** CreateTargetResponseV2

**example:** {"targetRid":"ri.gotham-artifact.0-0.target.example"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| targetRid | stringType | True |  |

**example:** {"targetRid":"ri.gotham-artifact.0-0.target.example"}
