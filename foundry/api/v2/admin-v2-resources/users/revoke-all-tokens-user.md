---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/users/revoke-all-tokens-user/"
title: "Revoke All Tokens User"
---
# Revoke All Tokens User

Revoke all active authentication tokens for the user including active browser sessions and long-lived development tokens. If the user has active sessions in a browser, this will force re-authentication. The caller must have permission to manage users for the target user's organization. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-write. Path parameters. A Foundry User ID. Examples. Error responses.
