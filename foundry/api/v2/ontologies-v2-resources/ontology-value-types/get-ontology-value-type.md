---
source_url: "https://www.palantir.com/docs/foundry/api/v2/ontologies-v2-resources/ontology-value-types/get-ontology-value-type/"
title: "Get Ontology Value Type"
---
# Get Ontology Value Type

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Gets a specific value type with the given API name. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:ontologies-read. Path parameters. The API name or RID of the Ontology. To find the API name or RID, use the List Ontologies endpoint or check the Ontology Manager. The API name of the value type. To find the API name, use the List value types endpoint or check the Ontology Manager. Query parameters. A boolean flag that, when set to true, enables the use of beta features in preview mode. Response body. Success response. The name of the value type in the API in camelCase format. The display name of the entity. Enum values: ACTIVE, DEPRECATED. Examples.
