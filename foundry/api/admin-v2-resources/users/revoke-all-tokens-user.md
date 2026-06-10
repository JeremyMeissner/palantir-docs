---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/users/revoke-all-tokens-user/"
title: "Revoke All Tokens User \u2022 API Reference"
---
# Revoke All Tokens User

## Endpoint

Revoke all active authentication tokens for the user including active browser sessions and long-lived 
development tokens. If the user has active sessions in a browser, this will force re-authentication.

The caller must have permission to manage users for the target user's organization.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.revokeAllTokensUser

**path:** /api/v2/admin/users/{userId}/revokeAllTokens

### Operation Type

### Scopes

| name |
| --- |
| api:admin-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| userId | stringType | True | A Foundry User ID. |

### Error Responses

| name | description |
| --- | --- |
| UserDeleted | The user is deleted. |
| RevokeAllTokensUserPermissionDenied | Could not revokeAllTokens the User. |
| UserNotFound | The given User could not be found. |
