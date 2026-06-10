---
source_url: "https://www.palantir.com/docs/gotham/api/revdb-resources/resolution/get-resolution-metadata/"
title: "Get resolution metadata \u2022 API Reference"
---
# Get resolution metadata

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Get metadata from previously-performed resolutions. If the object has not been resolved, the 
`canonicalObjectPrimaryKey` and `winnerObjectPrimaryKey` will be identical, and the `otherObjectPrimaryKeys`
will be empty.

**operationId:** v1.getResolutionMetadata

**path:** /api/gotham/v1/objects/{primaryKey}/resolution

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| primaryKey | stringType | True | The primary key of the requested object. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Response

#### Body

The resolution metadata the resolved object.

**name:** GetResolutionMetadataResponse

**example:** {"canonicalObjectPrimaryKey":"ri.gotham.111111-0.object-internal.111111","winnerObjectPrimaryKey":"ri.gotham.111111-0.object-internal.333333","otherObjectPrimaryKeys":["ri.gotham.111111-0.object-internal.222222"]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| canonicalObjectPrimaryKey | stringType | True | The primary key/unique identifier of an object, useful for interacting with Gotham APIs to load and mutate objects. |
| winnerObjectPrimaryKey | stringType | True | The primary key/unique identifier of an object, useful for interacting with Gotham APIs to load and mutate objects. |
| otherObjectPrimaryKeys | listType | False | All other sub-objects which compose this resolved object. This may include other winner object keys if some sub-objects have themselves been resolved. |

**example:** {"canonicalObjectPrimaryKey":"ri.gotham.111111-0.object-internal.111111","winnerObjectPrimaryKey":"ri.gotham.111111-0.object-internal.333333","otherObjectPrimaryKeys":["ri.gotham.111111-0.object-internal.222222"]}
