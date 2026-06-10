---
source_url: "https://www.palantir.com/docs/foundry/api/v2/ontologies-v2-resources/ontologies/get-ontology-full-metadata/"
parquet_url: "/foundry/api/v2/ontologies-v2-resources/ontologies/get-ontology-full-metadata/"
title: "Get Ontology Full Metadata"
fetched_at: "2026-05-12T19:34:37.610Z"
---
Get Ontology Full Metadata. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Get the full Ontology metadata. This includes the objects, links, actions, queries, and interfaces. This endpoint is designed to return as much metadata as possible in a single request to support OSDK workflows. It may omit certain entities rather than fail the request. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:ontologies-read. Path parameters. The API name or RID of the Ontology. To find the API name or RID, use the List Ontologies endpoint or check the Ontology Manager. Query parameters. The Foundry branch to load metadata from. If not specified, the default branch will be used. Branches are an experimental feature and not all workflows are supported. Response body. Success response. Metadata about an Ontology. Metadata about a Foundry branch. Examples.
