---
source_url: "https://www.palantir.com/docs/gotham/api/revdb-resources/resolution/unresolve-objects/"
title: "Unresolve objects \u2022 API Reference"
---
# Unresolve objects

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Unresolves objects from each other.

**operationId:** v1.unresolveObjects

**path:** /api/gotham/v1/objects/{primaryKey}/resolution/unresolve

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| primaryKey | stringType | True | The primary key of the object to unresolve sub-objects from. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| unresolveObjectPrimaryKeys | listType | False | The primary key of the constituent objects to unresolve. This list must contain only objects which are sub-objects of the resolved object. It must have at least one object, and may not contain the resolved object. |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Response

#### Body

The primary keys for each of the unresolved objects.

**name:** body

**example:** ["ri.gotham.111111-0.object-internal.111111","ri.gotham.111111-0.object-internal.222222"]

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| ObjectPrimaryKey | stringType | True | The primary key/unique identifier of an object, useful for interacting with Gotham APIs to load and mutate objects. |

**example:** ["ri.gotham.111111-0.object-internal.111111","ri.gotham.111111-0.object-internal.222222"]
