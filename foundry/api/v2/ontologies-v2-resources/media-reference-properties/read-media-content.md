---
source_url: "https://www.palantir.com/docs/foundry/api/v2/ontologies-v2-resources/media-reference-properties/read-media-content/"
title: "Read Media Content"
---
# Read Media Content

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Gets the content of a media item referenced by this property. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:ontologies-read. Path parameters. The API name or RID of the Ontology. To find the API name or RID, use the List Ontologies endpoint or check the Ontology Manager. The API name of the object type. To find the API name, use the List object types endpoint or check the Ontology Manager. The primary key of the object with the media reference property. The API name of the media reference property. To find the API name, check the Ontology Manager or use the Get object type endpoint. Query parameters. The package rid of the generated SDK. The version of the generated SDK. A boolean flag that, when set to true, enables the use of beta features in preview mode. Response body. The content stream. Examples.
