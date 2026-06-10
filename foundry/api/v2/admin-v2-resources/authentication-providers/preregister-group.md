---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/authentication-providers/preregister-group/"
title: "Preregister Group"
---
# Preregister Group

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Register a Group with a given name before any users with this group log in through this Authentication Provider. Preregistered groups can be used anywhere other groups are used in the platform. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-write. Path parameters. Query parameters. Enables the use of preview functionality. Request body. The name of the Group. The RIDs of the Organizations that can view this group. Response body. The ID of a Foundry Group or User. Examples. Error responses.
