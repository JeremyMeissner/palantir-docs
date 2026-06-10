---
source_url: "https://www.palantir.com/docs/foundry/api/v1/ontology-resources/objects/aggregate-objects/"
parquet_url: "/foundry/api/v1/ontology-resources/objects/aggregate-objects/"
title: "Aggregate Objects"
fetched_at: "2026-05-12T19:34:37.523Z"
---
Aggregate Objects. Perform functions on object fields in the specified ontology and object type. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:ontologies-read. Path parameters. The unique Resource Identifier (RID) of the Ontology that contains the objects. The type of the object to aggregate on. Request body. Response body. Success response. The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the nextPageToken field of the previous response and use it to populate the pageToken field of the next request. Examples.
