---
source_url: "https://www.palantir.com/docs/gotham/api/gaia-v2-resources/maps/search-maps/"
title: "Search Maps \u2022 API Reference"
---
# Search Maps

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Retrieves all published maps containing the mapName (does not have to be exact).

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:map-read`.

**operationId:** v2.searchMaps

**path:** /api/v2/gaia/maps/search

### Operation Type

### Scopes

| name |
| --- |
| api:map-read |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mapName | stringType | True | The name of the map(s) to be queried. |
| pageSize | integerType | False | The maximum number of matching Gaia maps to return. Defaults to 50. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

The response body containing the queried Gaia maps

**name:** SearchMapsResponse

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. api-gateway's Core.PageToken is an immutable @Unsafe String, which is incompatible with Gaia's backend search. This is a custom PageToken that is an immutable @Safe String. |

### Error Responses

| name | description |
| --- | --- |
| ErrorConvertingAppData | Failed to convert MapAppData from artifact appData to gaia MapAppData |
| SearchMapsPermissionDenied | Could not search the Map. |
