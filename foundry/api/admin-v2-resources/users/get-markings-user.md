---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/users/get-markings-user/"
title: "Get Markings User \u2022 API Reference"
---
# Get Markings User

## Endpoint

Retrieve Markings that the user is currently a member of.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.getMarkingsUser

**path:** /api/v2/admin/users/{userId}/getMarkings

### Operation Type

### Scopes

| name |
| --- |
| api:admin-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| userId | stringType | True | A Foundry User ID. |

### Response

#### Body

**name:** GetUserMarkingsResponse

**example:** {"view":["18212f9a-0e63-4b79-96a0-aae04df23336"]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| view | listType | False | The markings that the user has access to. The user will be able to access resources protected with these markings. This includes organization markings for organizations in which the user is a guest member. |

**example:** {"view":["18212f9a-0e63-4b79-96a0-aae04df23336"]}

### Error Responses

| name | description |
| --- | --- |
| UserDeleted | The user is deleted. |
| GetMarkingsUserPermissionDenied | Could not getMarkings the User. |
| UserNotFound | The given User could not be found. |
