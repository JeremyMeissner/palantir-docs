---
source_url: "https://www.palantir.com/docs/gotham/api/revdb-resources/objects/get-object-properties/"
title: "Get object properties \u2022 API Reference"
---
# Get object properties

## Endpoint

Return the full object property details for an object with the given primary key.
Full property details includes ID, in addition to value. If the object exists.

**operationId:** v1.getObjectProperties

**path:** /api/gotham/v1/objects/{primaryKey}/properties

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| primaryKey | stringType | True | The primary key of the requested object. |

### Response

#### Body

Property details response

**name:** GetPropertiesResponse

**example:** {"properties":[{"propertyId":"abc123","propertyType":"com.palantir.property.name","value":{"FIRST_NAME":"John","LAST_NAME":"Smith"}},{"propertyId":"def456","propertyType":"com.palantir.property.age","value":37}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| properties | listType | False |  |
| securityDetails | mapType | False |  |

**example:** {"properties":[{"propertyId":"abc123","propertyType":"com.palantir.property.name","value":{"FIRST_NAME":"John","LAST_NAME":"Smith"}},{"propertyId":"def456","propertyType":"com.palantir.property.age","value":37}]}
