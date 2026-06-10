---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/authentication-providers/preregister-group/"
title: "Preregister Group \u2022 API Reference"
---
# Preregister Group

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Register a Group with a given name before any users with this group log in through this Authentication Provider.
Preregistered groups can be used anywhere other groups are used in the platform.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.preregisterGroup

**path:** /api/v2/admin/enrollments/{enrollmentRid}/authenticationProviders/{authenticationProviderRid}/preregisterGroup

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

**name:** PreregisterGroupRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| name | stringType | True | The name of the Group. |
| organizations | listType | False | The RIDs of the Organizations that can view this group. |

**example:** {"name":"Data Source Admins","organizations":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"]}

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
| PreregisterGroupPermissionDenied | Could not preregisterGroup the AuthenticationProvider. |
| AuthenticationProviderNotFound | The given AuthenticationProvider could not be found. |
