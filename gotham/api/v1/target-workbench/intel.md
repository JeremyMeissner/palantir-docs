---
source_url: "https://www.palantir.com/docs/gotham/api/v1/target-workbench/intel/"
title: "Create Intel On a Target \u2022 API Reference"
---
# Create Intel On a Target

## Endpoint

Create Intel on Target by RID

**operationId:** v1.createTargetIntelV2

**path:** /api/gotham/v1/twb/createTargetIntel/{rid}

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

**name:** CreateTargetIntelRequest

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

**example:** {"id":"Example Intel Id","name":"Example Intel Name","description":"Intel containing location.","domain":"GEOINT","validTime":"2023-10-04T14:48:00.000Z","location":{"center":{"longitude":0.0,"latitude":0.0,"elevation":0.0},"radius":1.1},"confidence":3.0,"intelType":{"type":"geotimeObservation","geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example"},"source":"Example source"}

### Response

#### Body

Success response.

**name:** EmptySuccessResponse
