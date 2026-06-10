---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/users/delete-user/"
title: "Delete User \u2022 API Reference"
---
# Delete User

## Endpoint

Delete the User with the specified id.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.deleteUser

**path:** /api/v2/admin/users/{userId}

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
| DeleteUserPermissionDenied | Could not delete the User. |
| UserNotFound | The given User could not be found. |
