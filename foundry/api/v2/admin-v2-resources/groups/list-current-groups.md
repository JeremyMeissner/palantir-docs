---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/groups/list-current-groups/"
title: "List Current Groups"
---
# List Current Groups

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Returns all Groups which contain the current user as a direct or transitive member. For example if the current user is a member of Group A and Group A is a member of Group B, this endpoint will return Group A and Group B. Unlike the list Group Memberships endpoint which requires the api:admin-read scope, this endpoint does not require any particular scopes and can be used by any authenticated user to retrieve their own group memberships. Query parameters. Enables the use of preview functionality. Response body. Examples. Error responses.
