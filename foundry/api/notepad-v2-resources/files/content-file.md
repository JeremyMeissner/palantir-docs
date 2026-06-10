---
source_url: "https://www.palantir.com/docs/foundry/api/notepad-v2-resources/files/content-file/"
title: "Content File \u2022 API Reference"
---
# Content File

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Download file content.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:notepad-export`.

**operationId:** v2.contentFile

**path:** /api/v2/notepad/files/{fileRid}/content

### Operation Type

### Scopes

| name |
| --- |
| api:notepad-export |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| fileRid | stringType | True | The unique identifier for a File |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** body

##### Format

### Error Responses

| name | description |
| --- | --- |
| ContentFilePermissionDenied | Could not content the File. |
