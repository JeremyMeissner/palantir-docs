---
source_url: "https://www.palantir.com/docs/foundry/api/v2/ontologies-v2-resources/action-types/get-action-type-by-rid/"
title: "Get Action Type By Rid"
---
# Get Action Type By Rid

Gets a specific action type with the given RID. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:ontologies-read. Path parameters. The API name or RID of the Ontology. To find the API name or RID, use the List Ontologies endpoint or check the Ontology Manager. The RID of the action type. Query parameters. The Foundry branch to load the action type definition from. If not specified, the default branch will be used. Branches are an experimental feature and not all workflows are supported. Response body. Success response. The name of the action type in the API. To find the API name for your Action Type, use the List action types endpoint or check the Ontology Manager. The display name of the entity. The release status of the entity. Enum values: ACTIVE, ENDORSED, EXPERIMENTAL, DEPRECATED. The unique resource identifier of an action type, useful for interacting with other Foundry APIs. Optional description intended for tool use contexts, such as AI agents. Examples.
