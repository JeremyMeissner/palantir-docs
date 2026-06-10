---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/attachments/upload-attachment/"
title: "Upload Attachment \u2022 API Reference"
---
# Upload Attachment

## Endpoint

Upload an attachment to use in an action. Any attachment which has not been linked to an object via
an action within one hour after upload will be removed.
Previously mapped attachments which are not connected to any object anymore are also removed on
a biweekly basis.
The body of the request must contain the binary content of the file and the `Content-Type` header must be `application/octet-stream`.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-write`.

**operationId:** v2.uploadAttachmentV2

**path:** /api/v2/ontologies/attachments/upload

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-write |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| filename | stringType | True | The name of the file being uploaded. |

### Request

#### Body

**name:** body

##### Format

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
