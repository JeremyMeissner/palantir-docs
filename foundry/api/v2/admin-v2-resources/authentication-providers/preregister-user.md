---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/authentication-providers/preregister-user/"
parquet_url: "/foundry/api/v2/admin-v2-resources/authentication-providers/preregister-user/"
title: "Preregister User"
fetched_at: "2026-05-12T19:34:37.748Z"
---
Preregister User. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Register a User with a given username before they log in to the platform for the first time through this Authentication Provider. Preregistered users can be assigned to groups and roles prior to first login. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-write. Path parameters. Query parameters. Enables the use of preview functionality. Request body. The new user's username. This must match one of the provider's supported username patterns. The RID of the user's primary Organization. This may be changed when the user logs in for the first time depending on any configured Organization assignment rules. Response body. The ID of a Foundry Group or User. Examples. Error responses.
