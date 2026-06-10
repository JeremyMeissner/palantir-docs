---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/media-reference-properties/upload-media-content/"
title: "Upload Media Content \u2022 API Reference"
---
# Upload Media Content

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Uploads a media item to the media set which backs the specified property.  The property must be backed by a single media set and branch, otherwise an error will be thrown.
The body of the request must contain the binary content of the file and the `Content-Type` header must be `application/octet-stream`.

Third-party applications using this endpoint via OAuth2 must request the following operation scopes: `api:ontologies-read api:ontologies-write`.

**operationId:** v2.uploadMediaContent

**path:** /api/v2/ontologies/{ontology}/objectTypes/{objectType}/media/{property}/upload

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |
| api:ontologies-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The API name or RID of the Ontology. To find the API name or RID, use the **List Ontologies** endpoint or check the **Ontology Manager**. |
| objectType | stringType | True | The API name of the object type. To find the API name, use the **List object types** endpoint or check the **Ontology Manager**. |
| property | stringType | True | The API name of the media reference property. To find the API name, check the **Ontology Manager** or use the **Get object type** endpoint. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mediaItemPath | stringType | False | A path for the media item within its backing media set. Required if the backing media set requires paths. |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |

### Request

#### Body

**name:** body

##### Format

### Response

#### Body

The media reference for the uploaded media.

**name:** MediaReference

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| mimeType | stringType | True | The [media type](https://www.iana.org/assignments/media-types/media-types.xhtml) of the file or attachment. Examples: `application/json`, `application/pdf`, `application/octet-stream`, `image/jpeg` |
| reference | unionType | True | A union of the types supported by media reference properties. |
