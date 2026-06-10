---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/authentication-providers/preregister-user/"
title: "Preregister User \u2022 API Reference"
---
# Preregister User

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Register a User with a given username before they log in to the platform for the first time through this
Authentication Provider. Preregistered users can be assigned to groups and roles prior to first login.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.preregisterUser

**path:** /api/v2/admin/enrollments/{enrollmentRid}/authenticationProviders/{authenticationProviderRid}/preregisterUser

### Operation Type

### Scopes

| name |
| --- |
| api:admin-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| enrollmentRid | stringType | True |  |
| authenticationProviderRid | stringType | True |  |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** PreregisterUserRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| username | stringType | True | The new user's username. This must match one of the provider's supported username patterns. |
| organization | stringType | True | The RID of the user's primary Organization. This may be changed when the user logs in for the first time depending on any configured Organization assignment rules. |
| givenName | stringType | False |  |
| familyName | stringType | False |  |
| email | stringType | False |  |
| attributes | mapType | False |  |

**example:** {"organization":"ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa","givenName":"John","familyName":"Smith","attributes":{"department":["Finance"],"jobTitle":["Accountant"]},"email":"jsmith@example.com","username":"jsmith"}

### Response

#### Body

The ID of a Foundry Group or User.

**name:** PrincipalId

##### Format

**example:** f05f8da4-b84c-4fca-9c77-8af0b13d11de

**example:** f05f8da4-b84c-4fca-9c77-8af0b13d11de

### Error Responses

| name | description |
| --- | --- |
| PreregisterUserPermissionDenied | Could not preregisterUser the AuthenticationProvider. |
| AuthenticationProviderNotFound | The given AuthenticationProvider could not be found. |
