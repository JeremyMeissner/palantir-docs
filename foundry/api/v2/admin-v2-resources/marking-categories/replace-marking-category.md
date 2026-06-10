---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/marking-categories/replace-marking-category/"
parquet_url: "/foundry/api/v2/admin-v2-resources/marking-categories/replace-marking-category/"
title: "Replace Marking Category"
fetched_at: "2026-05-12T19:34:37.728Z"
---
Replace Marking Category. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Replace the MarkingCategory with the specified id. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-write. Path parameters. The ID of a marking category. For user-created categories, this will be a UUID. Markings associated with Organizations are placed in a category with ID "Organization". Query parameters. Enables the use of preview functionality. Request body. Response body. The replaced MarkingCategory. The ID of a marking category. For user-created categories, this will be a UUID. Markings associated with Organizations are placed in a category with ID "Organization". Enum values: CONJUNCTIVE, DISJUNCTIVE. Enum values: MANDATORY, CBAC. The time at which the resource was created. The Foundry user who created this resource. Examples. Error responses.
