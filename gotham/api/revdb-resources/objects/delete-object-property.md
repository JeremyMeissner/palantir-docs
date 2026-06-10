---
source_url: "https://www.palantir.com/docs/gotham/api/revdb-resources/objects/delete-object-property/"
title: "Delete object property \u2022 API Reference"
---
# Delete object property

## Endpoint

Delete a specific property from an object instance.

**operationId:** v1.deleteObjectProperty

**path:** /api/gotham/v1/objects/{primaryKey}/properties/{propertyId}

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| primaryKey | stringType | True | The primary key of the object to delete a property from. |
| propertyId | stringType | True | The unique identifier of the property to be deleted. |

### Response

#### Body

Empty response indicating success.

**name:** EmptySuccessResponse
