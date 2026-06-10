---
source_url: "https://www.palantir.com/docs/gotham/api/revdb-resources/objects/create-object/"
title: "Create object \u2022 API Reference"
---
# Create object

## Endpoint

Creates an object for the given object type.

By default, all "representative" property types must be specified for the requested object type to be created successfully.
If any representative properties are missing on initial creation,
a [MissingRepresentativePropertyTypes](/docs/gotham/api/general/overview/errors#objects-errors) error
will be raised with the missing property types as an argument.

**operationId:** v1.createObject

**path:** /api/gotham/v1/objects/types/{objectType}

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| objectType | stringType | True | The type of object to create. |

### Request

#### Body

**name:** CreateObjectRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| title | stringType | False | Initial title for created object; may be omitted, in which case a "default" title is assigned. |
| properties | listType | False | Initial property values to add during creation; may be left empty, in which case the object will begin with no properties. |
| security | objectType | True | Security mutation details for a component of an object - property, media, link. Specifying security overrides the system's default security when creating and updating data. If portion markings are specified, permissions *may* be specified. If portion markings are not specified, permissions *must* be specified.  This model may evolve over time for other security features. |
| validationMode | enumType | False | Validation mode when mutating Object instances. Defaults to `STRICT` if not specified.  `STRICT` mode strictly enforces ontology compliance: - All representative property types must be specified when creating an object. - No disallowed property types may be specified when creating an object or adding to an object. - Property values for enumeration property types must be a valid enum instance.  `LENIENT` mode enforces that object / property / link types exist. |

**example:** {"title":"John Smith","properties":[{"propertyType":"com.palantir.property.name","value":{"FIRST_NAME":"John","LAST_NAME":"Smith"}},{"propertyType":"com.palantir.property.age","value":24}],"security":{"portionMarkings":["SENSITIVE"]}}

### Response

#### Body

Success response

**name:** CreateObjectResponse

**example:** {"primaryKey":"ri.gotham.111111-0.object-internal.111111"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| primaryKey | stringType | True | The primary key/unique identifier of an object, useful for interacting with Gotham APIs to load and mutate objects. |

**example:** {"primaryKey":"ri.gotham.111111-0.object-internal.111111"}
