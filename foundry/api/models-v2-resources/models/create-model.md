---
source_url: "https://www.palantir.com/docs/foundry/api/models-v2-resources/models/create-model/"
title: "Create Model \u2022 API Reference"
---
# Create Model

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Creates a new Model with no versions.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:models-write`.

**operationId:** v2.createModel

**path:** /api/v2/models

### Operation Type

### Scopes

| name |
| --- |
| api:models-write |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** CreateModelRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| name | stringType | True |  |
| parentFolderRid | stringType | True | The unique resource identifier (RID) of a Folder. |

**example:** {"parentFolderRid":"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791","name":"House Pricing Model"}

### Response

#### Body

The created Model

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
| ResourceNameAlreadyExists | The provided resource name is already in use by another resource in the same folder. |
| InvalidDisplayName | The display name of a Resource should not be exactly `.` or `..`, contain a forward slash `/` and must be less than or equal to 700 characters. |
| CreateModelPermissionDenied | Could not create the Model. |
