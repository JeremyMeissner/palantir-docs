---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/markings/parse-classifications/"
title: "Parse Classifications \u2022 API Reference"
---
# Parse Classifications

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Parses classification marking strings (e.g. 'S//NF') into their component marking IDs. Strings that cannot be parsed are returned in 'errors' with a human-readable message.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.parseClassifications

**path:** /api/v2/admin/markings/parseClassifications

### Operation Type

### Scopes

| name |
| --- |
| api:admin-read |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** ParseClassificationsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| classificationStrings | listType | False | The classification strings to parse, e.g. 'S//NF'. Duplicate entries are ignored. At most 1000 entries are accepted. |

**example:** {"classificationStrings":["MTS//MNF","MU"]}

### Response

#### Body

**name:** ParseClassificationsResponse

**example:** {"parsed":{"MTS//MNF":["MNF","MTS"]},"errors":{"INVALID_MARKING":"Unknown marking: INVALID_MARKING"}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| parsed | mapType | False | Map of valid classification strings to their component marking IDs. Strings that could not be parsed are absent from this map and appear in 'errors' instead. |
| errors | mapType | False | Map of classification strings that could not be parsed to a human-readable error message. |

**example:** {"parsed":{"MTS//MNF":["MNF","MTS"]},"errors":{"INVALID_MARKING":"Unknown marking: INVALID_MARKING"}}

### Error Responses

| name | description |
| --- | --- |
| ParseClassificationsPermissionDenied | The provided token does not have permission to parse the given classification strings. |
| CbacUnavailable | CBAC is not available. |
