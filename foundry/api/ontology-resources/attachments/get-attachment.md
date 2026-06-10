---
source_url: "https://www.palantir.com/docs/foundry/api/ontology-resources/attachments/get-attachment/"
title: "Get Attachment \u2022 API Reference"
---
# Get Attachment

## Endpoint

Get the metadata of an attachment.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v1.getAttachment

**path:** /api/v1/attachments/{attachmentRid}

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| attachmentRid | stringType | True | The RID of the attachment. |

### Response

#### Body

Success response.

**name:** Attachment

**example:** {"rid":"ri.attachments.main.attachment.bb32154e-e043-4b00-9461-93136ca96b6f","filename":"My Image.jpeg","sizeBytes":393469,"mediaType":"image/jpeg"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The unique resource identifier of an attachment. |
| filename | stringType | True | The name of a File within Foundry. Examples: `my-file.txt`, `my-file.jpg`, `dataframe.snappy.parquet`. |
| sizeBytes | stringType | True | The size of the file or attachment in bytes. |
| mediaType | stringType | True | The [media type](https://www.iana.org/assignments/media-types/media-types.xhtml) of the file or attachment. Examples: `application/json`, `application/pdf`, `application/octet-stream`, `image/jpeg` |

**example:** {"rid":"ri.attachments.main.attachment.bb32154e-e043-4b00-9461-93136ca96b6f","filename":"My Image.jpeg","sizeBytes":393469,"mediaType":"image/jpeg"}
