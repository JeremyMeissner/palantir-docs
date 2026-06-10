---
source_url: "https://www.palantir.com/docs/gotham/api/revdb-resources/objects/add-object-property/"
title: "Add property to object \u2022 API Reference"
---
# Add property to object

## Endpoint

Add a new property value to an existing object.

**operationId:** v1.addObjectProperty

**path:** /api/gotham/v1/objects/{primaryKey}/properties

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| primaryKey | stringType | True | The primary key of the object to add a property to. |

### Request

#### Body

Adds a property to an existing object. This is similar but different from an initial
creation in that it *does* require security to be specified.

**name:** AddPropertyRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| propertyType | stringType | True | The name of the property in the API - also called the Property Type URI. |
| value | anyType | True | Represents the value of a property. The following table provides expected representations of scalar data types:  \| Type      \| JSON encoding                                         \| Example                         \| \|-----------\|-------------------------------------------------------\|---------------------------------\| \| Date      \| ISO 8601 extended local date string                   \| `"2021-05-01"`                  \| \| Decimal   \| string                                                \| `"2.718281828"`                 \| \| Double    \| number                                                \| `3.14159265`                    \| \| Integer   \| number                                                \| `238940`                        \| \| Long      \| string                                                \| `"58319870951433"`              \| \| String    \| string                                                \| `"Call me Ishmael"`             \| \| Timestamp \| ISO 8601 extended offset date-time string in UTC zone \| `"2021-01-04T05:00:00Z"`        \| |
| security | objectType | True | Security mutation details for a component of an object - property, media, link. Specifying security overrides the system's default security when creating and updating data. If portion markings are specified, permissions *may* be specified. If portion markings are not specified, permissions *must* be specified.  This model may evolve over time for other security features. |

**example:** {"propertyType":"com.palantir.property.name","value":{"FIRST_NAME":"John","LAST_NAME":"Smith"},"security":{"portionMarkings":["SENSITIVE"]}}

### Response

#### Body

Success response

**name:** EmptySuccessResponse
