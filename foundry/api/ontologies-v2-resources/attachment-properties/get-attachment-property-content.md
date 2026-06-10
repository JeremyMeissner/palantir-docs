---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/attachment-properties/get-attachment-property-content/"
title: "Get Attachment Property Content \u2022 API Reference"
---
# Get Attachment Property Content

## Endpoint

Get the content of an attachment.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.getAttachmentPropertyContentV2

**path:** /api/v2/ontologies/{ontology}/objects/{objectType}/{primaryKey}/attachments/{property}/content

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
| primaryKey | stringType | True | The primary key of the object containing the attachment. |
| property | stringType | True | The API name of the attachment property. To find the API name for your attachment, check the **Ontology Manager** or use the **Get object type** endpoint. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| sdkPackageRid | stringType | False | The package rid of the generated SDK. |
| sdkVersion | stringType | False | The version of the generated SDK. |

### Response

#### Body

Success response.

**name:** body

##### Format
