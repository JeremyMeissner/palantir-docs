---
source_url: "https://www.palantir.com/docs/gotham/api/revdb-resources/objects/get-object/"
title: "Get object \u2022 API Reference"
---
# Get object

## Endpoint

Gets a specific object with the given primary key.

**operationId:** v1.getObject

**path:** /api/gotham/v1/objects/{primaryKey}

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| primaryKey | stringType | True | The primary key of the requested object. |

### Response

#### Body

Success response

**name:** GetObjectResponse

**example:** {"primaryKey":"ri.gotham.111111-0.object-internal.111111","objectType":"com.palantir.object.person","properties":{"com.palantir.property.name":[{"FIRST_NAME":"John","LAST_NAME":"Smith"}],"com.palantir.property.age":[37]}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| primaryKey | stringType | True | The primary key/unique identifier of an object, useful for interacting with Gotham APIs to load and mutate objects. |
| title | stringType | False | The title of an object, which represents a display-friendly String of what the object represents. |
| objectType | stringType | True | The name of the object in the API - also called the Object Type URI. |
| properties | mapType | False | A map of the property values of the object. |
| intrinsicCoordinates | objectType | False |  |
| timeInterval | objectType | False | Represents a time interval by its start and end datetime. `TimeInterval` is generally used when an Object has a meaningful start and/or end datetime, such as an event.  For example, a Meeting might have start and end datetimes corresponding to when the meeting began and ended. |

**example:** {"primaryKey":"ri.gotham.111111-0.object-internal.111111","objectType":"com.palantir.object.person","properties":{"com.palantir.property.name":[{"FIRST_NAME":"John","LAST_NAME":"Smith"}],"com.palantir.property.age":[37]}}
