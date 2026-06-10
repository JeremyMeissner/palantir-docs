---
source_url: "https://www.palantir.com/docs/foundry/api/models-v2-resources/models/get-model/"
title: "Get Model \u2022 API Reference"
---
# Get Model

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Retrieves a Model by its Resource Identifier (RID).

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:models-read`.

**operationId:** v2.getModel

**path:** /api/v2/models/{modelRid}

### Operation Type

### Scopes

| name |
| --- |
| api:models-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| modelRid | stringType | True | The Resource Identifier (RID) of a Model. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** Model

**example:** {"rid":"ri.models.main.model.f351c142-0e4c-4b12-adc2-6e1539737ae9"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The Resource Identifier (RID) of a Model. |

**example:** {"rid":"ri.models.main.model.f351c142-0e4c-4b12-adc2-6e1539737ae9"}

### Error Responses

| name | description |
| --- | --- |
| ModelNotFound | The given Model could not be found. |
