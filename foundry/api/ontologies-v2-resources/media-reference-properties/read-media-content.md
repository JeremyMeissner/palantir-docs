---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/media-reference-properties/read-media-content/"
title: "Read Media Content \u2022 API Reference"
---
# Read Media Content

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Gets the content of a media item referenced by this property.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.readMediaContent

**path:** /api/v2/ontologies/{ontology}/objects/{objectType}/{primaryKey}/media/{property}/content

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The API name or RID of the Ontology. To find the API name or RID, use the **List Ontologies** endpoint or check the **Ontology Manager**. |
| objectType | stringType | True | The API name of the object type. To find the API name, use the **List object types** endpoint or check the **Ontology Manager**. |
| primaryKey | stringType | True | The primary key of the object with the media reference property. |
| property | stringType | True | The API name of the media reference property. To find the API name, check the **Ontology Manager** or use the **Get object type** endpoint. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| sdkPackageRid | stringType | False | The package rid of the generated SDK. |
| sdkVersion | stringType | False | The version of the generated SDK. |
| branch | stringType | False | The Foundry branch to read from. If not specified, the default branch will be used. |
| preview | booleanType | False | A boolean flag that, when set to true, enables the use of beta features in preview mode. |

### Response

#### Body

The content stream.

**name:** body

##### Format
