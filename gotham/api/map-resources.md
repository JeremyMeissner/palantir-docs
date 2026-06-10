---
source_url: "https://www.palantir.com/docs/gotham/api/map-resources/"
title: "Export Map as KMZ \u2022 API Reference"
---
# Export Map as KMZ

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Export all map elements from a Gaia map to a KMZ file suitable for rendering in external applications, such as Google Earth. There are no schema compatibility guarantees provided for internal KMZ content exported by this endpoint.
Only local map elements will be exported i.e. no elements from linked maps.

**operationId:** v1.exportKmz

**path:** /api/gotham/v1/maps/{mapId}/kmz

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mapId | stringType | True | The artifact identifier of the Gaia map being exported, which can be copied via **Help** > **Developer** > **Copy id**. The export call will download all elements in the referenced map. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

The request body to export elements to a KMZ/SHP file.

**name:** GaiaExportRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| name | stringType | False | The name of the exported file. Defaults to 'palantir-export'. |

**example:** {"name":"Example file name"}

### Response

#### Body

Success response.

**name:** body

##### Format
