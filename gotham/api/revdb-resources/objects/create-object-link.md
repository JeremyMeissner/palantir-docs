---
source_url: "https://www.palantir.com/docs/gotham/api/revdb-resources/objects/create-object-link/"
title: "Create object link \u2022 API Reference"
---
# Create object link

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Create a link.  Both sides of the link must exist.

Invalid link type result in an [InvalidOntologyTypes error](/docs/gotham/api/general/overview/errors#objects-errors).

**operationId:** v1.createObjectLink

**path:** /api/gotham/v1/objects/{primaryKey}/links/{linkType}

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| primaryKey | stringType | True | The primary key of the object from which the links originate (source object). |
| linkType | stringType | True | The type of the link that exists between the object and the requested objects. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

A request to create a link to a target object. Requires specifying the
security for the link to create, which may be different from one or both sides
of the objects being linked.

**name:** CreateObjectLinkRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| targetPrimaryKey | stringType | True | The primary key/unique identifier of an object, useful for interacting with Gotham APIs to load and mutate objects. |
| security | objectType | True | Security mutation details for a component of an object - property, media, link. Specifying security overrides the system's default security when creating and updating data. If portion markings are specified, permissions *may* be specified. If portion markings are not specified, permissions *must* be specified.  This model may evolve over time for other security features. |

**example:** {"targetPrimaryKey":"ri.gotham.111111-0.object-internal.222222","security":{"portionMarkings":["SENSITIVE"]}}

### Response

#### Body

Success response indicating link was created successfully.

**name:** CreateObjectLinkResponse
