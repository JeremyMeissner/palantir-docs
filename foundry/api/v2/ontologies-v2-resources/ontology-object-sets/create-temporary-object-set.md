---
source_url: "https://www.palantir.com/docs/foundry/api/v2/ontologies-v2-resources/ontology-object-sets/create-temporary-object-set/"
title: "Create Temporary Object Set"
---
# Create Temporary Object Set

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Creates a temporary ObjectSet from the given definition. This ObjectSet expires after one hour. Third-party applications using this endpoint via OAuth2 must request the following operation scopes: api:ontologies-read api:ontologies-write. Path parameters. The API name or RID of the Ontology. To find the API name or RID, use the List Ontologies endpoint or check the Ontology Manager. Query parameters. The Foundry branch to reference. If not specified, the default branch will be used. Branches are an experimental feature and not all workflows are supported. The package rid of the generated SDK. The package version of the generated SDK. Request body. Represents the definition of an ObjectSet in the Ontology. Response body. Success response. Examples.
