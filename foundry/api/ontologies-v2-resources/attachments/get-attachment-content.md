---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/attachments/get-attachment-content/"
title: "Get Attachment Content \u2022 API Reference"
---
# Get Attachment Content

## Endpoint

Get the content of an attachment.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v2.getAttachmentContentV2

**path:** /api/v2/ontologies/attachments/{attachmentRid}/content

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

**name:** body

##### Format
