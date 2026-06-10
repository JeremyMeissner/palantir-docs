---
source_url: "https://www.palantir.com/docs/foundry/api/v1/ontology-resources/attachments/upload-attachment/"
title: "Upload Attachment"
---
# Upload Attachment

Upload an attachment to use in an action. Any attachment which has not been linked to an object via an action within one hour after upload will be removed. Previously mapped attachments which are not connected to any object anymore are also removed on a biweekly basis. The body of the request must contain the binary content of the file and the Content-Type header must be application/octet-stream. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:ontologies-write. Query parameters. The name of the file being uploaded. Request body. Response body. Success response. The unique resource identifier of an attachment. The name of a File within Foundry. Examples: my-file.txt, my-file.jpg, dataframe.snappy.parquet. The size of the file or attachment in bytes. The media type of the file or attachment. Examples: application/json, application/pdf, application/octet-stream, image/jpeg. Examples.
