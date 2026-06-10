---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/markings/replace-marking/"
parquet_url: "/foundry/api/v2/admin-v2-resources/markings/replace-marking/"
title: "Replace Marking"
fetched_at: "2026-05-12T19:34:37.748Z"
---
Replace Marking. Replace the Marking with the specified id. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-write. Path parameters. The ID of a security marking. Request body. Response body. The replaced Marking. The ID of a security marking. The ID of a marking category. For user-created categories, this will be a UUID. Markings associated with Organizations are placed in a category with ID "Organization". If this marking is associated with an Organization, its RID will be populated here. The time at which the resource was created. The Foundry user who created this resource. Examples. Error responses.
