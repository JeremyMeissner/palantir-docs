---
source_url: "https://www.palantir.com/docs/foundry/api/v2/filesystem-v2-resources/resources/get-access-requirements/"
parquet_url: "/foundry/api/v2/filesystem-v2-resources/resources/get-access-requirements/"
title: "Get Access Requirements"
fetched_at: "2026-05-12T19:34:37.654Z"
---
Get Access Requirements. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Returns a list of access requirements a user needs in order to view a resource. Access requirements are composed of Organizations and Markings, and can either be applied directly to the resource or inherited. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:filesystem-read. Path parameters. The unique resource identifier (RID) of a Resource. Query parameters. Enables the use of preview functionality. Response body. Access requirements for a resource are composed of Markings and Organizations. Organizations are disjunctive, while Markings are conjunctive. Examples. Error responses.
