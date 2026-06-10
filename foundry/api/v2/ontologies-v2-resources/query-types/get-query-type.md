---
source_url: "https://www.palantir.com/docs/foundry/api/v2/ontologies-v2-resources/query-types/get-query-type/"
parquet_url: "/foundry/api/v2/ontologies-v2-resources/query-types/get-query-type/"
title: "Get Query Type"
fetched_at: "2026-05-12T19:34:37.607Z"
---
Get Query Type. Gets a specific query type with the given API name. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:ontologies-read. Path parameters. The API name or RID of the Ontology. To find the API name or RID, use the List Ontologies endpoint or check the Ontology Manager. The API name of the query type. To find the API name, use the List query types endpoint or check the Ontology Manager. Query parameters. The version of the Query to get. The package rid of the generated SDK. The version of the generated SDK. Response body. Success response. The name of the Query in the API. The display name of the entity. A union of all the types supported by Ontology Query parameters or outputs. The unique resource identifier of a Function, useful for interacting with other Foundry APIs. The version of the given Function, written <major>.<minor>.<patch>-<tag>, where -<tag> is optional. Examples: 1.2.3, 1.2.3-rc1. Examples.
