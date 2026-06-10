---
source_url: "https://www.palantir.com/docs/foundry/api/v2/ontologies-v2-resources/attachment-properties/get-attachment-property-by-rid/"
title: "Get Attachment Property By Rid"
---
# Get Attachment Property By Rid

Get the metadata of a particular attachment in an attachment list. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:ontologies-read. Path parameters. The API name or RID of the Ontology. To find the API name or RID, use the List Ontologies endpoint or check the Ontology Manager. The API name of the object type. To find the API name, use the List object types endpoint or check the Ontology Manager. The primary key of the object containing the attachment. The API name of the attachment property. To find the API name for your attachment, check the Ontology Manager or use the Get object type endpoint. The RID of the attachment. Query parameters. The package rid of the generated SDK. The version of the generated SDK. Response body. Success response. The unique resource identifier of an attachment. The name of a File within Foundry. Examples: my-file.txt, my-file.jpg, dataframe.snappy.parquet. The size of the file or attachment in bytes. The media type of the file or attachment. Examples: application/json, application/pdf, application/octet-stream, image/jpeg. Examples.
