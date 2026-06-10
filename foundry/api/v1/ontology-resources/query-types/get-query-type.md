---
source_url: "https://www.palantir.com/docs/foundry/api/v1/ontology-resources/query-types/get-query-type/"
title: "Get Query Type"
---
# Get Query Type

Gets a specific query type with the given API name. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:ontologies-read. Path parameters. The unique Resource Identifier (RID) of the Ontology that contains the query type. To look up your Ontology RID, please use the List ontologies endpoint or check the Ontology Manager. The API name of the query type. To find the API name, use the List query types endpoint or check the Ontology Manager. Response body. Success response. The name of the Query in the API. The display name of the entity. A union of all the primitive types used by Palantir's Ontology-based products. The unique resource identifier of a Function, useful for interacting with other Foundry APIs. The version of the given Function, written <major>.<minor>.<patch>-<tag>, where -<tag> is optional. Examples: 1.2.3, 1.2.3-rc1. Examples.
