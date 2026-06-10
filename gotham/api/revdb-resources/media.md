---
source_url: "https://www.palantir.com/docs/gotham/api/revdb-resources/media/"
title: "Get object media \u2022 API Reference"
---
# Get object media

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Get media metadata for object. Media metadata contains an identifier and other
attributes suitable for display/download, such as content type and title.

**operationId:** v1.getObjectMedia

**path:** /api/gotham/v1/objects/{primaryKey}/media

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

Success response

**name:** GetMediaResponse

**example:** {"media":[{"rid":"ri.gotham.111111-0.media-internal.111111.xtdsXlRMFmRRUdwQsD2kZOYOLY_2FS0VQ9SviNM6AJ_2FJM_3D","title":"myimage.jpg","description":"My Image Description","sizeBytes":10312,"mediaType":"image/jpeg"}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| media | listType | False |  |
| securityDetails | mapType | False |  |

**example:** {"media":[{"rid":"ri.gotham.111111-0.media-internal.111111.xtdsXlRMFmRRUdwQsD2kZOYOLY_2FS0VQ9SviNM6AJ_2FJM_3D","title":"myimage.jpg","description":"My Image Description","sizeBytes":10312,"mediaType":"image/jpeg"}]}
