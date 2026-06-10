---
source_url: "https://www.palantir.com/docs/gotham/api/revdb-resources/objects/update-object-property/"
title: "Update object property \u2022 API Reference"
---
# Update object property

## Endpoint

Update property details.  By default, writes to property values from multiple sources will fail.
To override this behavior, clients may specify to 'applyToAllSources', which defaults to false.
Clients must ensure this behavior matches expectations when changing multi-sourced property values.

If the property to update has multiple sources and applyToAllSources is not set to true,
UnclearMultiSourcePropertyUpdateRequest will be raised.  If setting applyToAllSources to true, ensure intention matches
expected result.

**operationId:** v1.updateObjectProperty

**path:** /api/gotham/v1/objects/{primaryKey}/properties/{propertyId}

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| primaryKey | stringType | True | The primary key of the requested object. |
| propertyId | stringType | True | The identifier of the property to update. |

### Request

#### Body

Request to update a specific property value.

**name:** UpdatePropertyRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| value | anyType | True | Represents the value of a property. The following table provides expected representations of scalar data types:  \| Type      \| JSON encoding                                         \| Example                         \| \|-----------\|-------------------------------------------------------\|---------------------------------\| \| Date      \| ISO 8601 extended local date string                   \| `"2021-05-01"`                  \| \| Decimal   \| string                                                \| `"2.718281828"`                 \| \| Double    \| number                                                \| `3.14159265`                    \| \| Integer   \| number                                                \| `238940`                        \| \| Long      \| string                                                \| `"58319870951433"`              \| \| String    \| string                                                \| `"Call me Ishmael"`             \| \| Timestamp \| ISO 8601 extended offset date-time string in UTC zone \| `"2021-01-04T05:00:00Z"`        \| |
| applyToAllSources | booleanType | False | Whether to update the property value across all sources if there are multiple. Defaults to false. If not specified or false, and existing property value has multiple sources, the write will fail. |

**example:** {"value":{"FIRST_NAME":"Johnny","LAST_NAME":"Smith"}}

### Response

#### Body

Success response

**name:** EmptySuccessResponse
