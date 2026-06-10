---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/attachment-properties/get-attachment-property-by-rid/"
title: "Get Attachment Property By Rid \u2022 API Reference"
---
# Get Attachment Property By Rid

## Endpoint

Get the metadata of a particular attachment in an attachment list.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.getAttachmentPropertyByRidV2

**path:** /api/v2/ontologies/{ontology}/objects/{objectType}/{primaryKey}/attachments/{property}/{attachmentRid}

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
| attachmentRid | stringType | True | The RID of the attachment. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| sdkPackageRid | stringType | False | The package rid of the generated SDK. |
| sdkVersion | stringType | False | The version of the generated SDK. |

### Response

#### Body

Success response.

**name:** AttachmentV2

**example:** {"rid":"ri.attachments.main.attachment.bb32154e-e043-4b00-9461-93136ca96b6f","filename":"My Image.jpeg","sizeBytes":393469,"mediaType":"image/jpeg"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The unique resource identifier of an attachment. |
| filename | stringType | True | The name of a File within Foundry. Examples: `my-file.txt`, `my-file.jpg`, `dataframe.snappy.parquet`. |
| sizeBytes | stringType | True | The size of the file or attachment in bytes. |
| mediaType | stringType | True | The [media type](https://www.iana.org/assignments/media-types/media-types.xhtml) of the file or attachment. Examples: `application/json`, `application/pdf`, `application/octet-stream`, `image/jpeg` |

**example:** {"rid":"ri.attachments.main.attachment.bb32154e-e043-4b00-9461-93136ca96b6f","filename":"My Image.jpeg","sizeBytes":393469,"mediaType":"image/jpeg"}
