---
source_url: "https://www.palantir.com/docs/gotham/api/target-workbench/intel/modify-target-intel/"
title: "Modify Intel On a Target \u2022 API Reference"
---
# Modify Intel On a Target

## Endpoint

Modify Intel on Target by RID and IntelId

**operationId:** v1.modifyTargetIntel

**path:** /api/gotham/v1/twb/modifyTargetIntel/{rid}

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

Request body to modify intel attached to a Target by TargetRID and IntelId.

**name:** ModifyTargetIntelRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| intel | listType | False |  |

**example:** {"intel":[{"id":"Example Intel Id","name":"Example Intel Name","description":"Intel containing location.","intelDomain":"GEOINT","validTime":"2023-10-04T14:48:00.000Z","location":{"center":{"longitude":0.0,"latitude":0.0,"elevation":0.0},"radius":1.1},"confidence":3.0,"intelType":{"type":"geotimeObservation","geotimeTrack":"ri.gotham.0-0.geotime-track.aa.bb.cc.example"}}]}

### Response

#### Body

Success response.

**name:** ModifyTargetIntelResponse

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| updatedIntelIds | listType | False |  |
