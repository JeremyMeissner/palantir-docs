---
source_url: "https://www.palantir.com/docs/gotham/api/revdb-resources/resolution/resolve-objects/"
title: "Resolve objects \u2022 API Reference"
---
# Resolve objects

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Resolves two or more objects together.

**operationId:** v1.resolveObjects

**path:** /api/gotham/v1/objects/{primaryKey}/resolution

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| primaryKey | stringType | True | The primary key of one object to resolve. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| resolvedObjectPrimaryKeys | listType | False | The primary key of the other objects to resolve. |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Response

#### Body

The primary key for the resolved object.

**name:** ObjectPrimaryKey

**example:** ri.gotham.111111-0.object-internal.111111

**example:** ri.gotham.111111-0.object-internal.111111
