---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/user-provider-infos/replace-user-provider-info/"
title: "Replace User Provider Info \u2022 API Reference"
---
# Replace User Provider Info

## Endpoint

Replace the UserProviderInfo.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.replaceUserProviderInfo

**path:** /api/v2/admin/users/{userId}/providerInfo

### Operation Type

### Scopes

| name |
| --- |
| api:admin-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| userId | stringType | True | A Foundry User ID. |

### Request

#### Body

**name:** ReplaceUserProviderInfoRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| providerId | stringType | True | The ID of the User in the external authentication provider. This value is determined by the authentication provider. At most one User can have a given provider ID in a given Realm. |

**example:** {"providerId":"2838c8f3-d76a-4e99-acf1-1dee537e4c48"}

### Response

#### Body

The replaced UserProviderInfo

**name:** UserProviderInfo

**example:** {"providerId":"2838c8f3-d76a-4e99-acf1-1dee537e4c48"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| providerId | stringType | True | The ID of the User in the external authentication provider. This value is determined by the authentication provider. At most one User can have a given provider ID in a given Realm. |

**example:** {"providerId":"2838c8f3-d76a-4e99-acf1-1dee537e4c48"}

### Error Responses

| name | description |
| --- | --- |
| GetUserProviderInfoPermissionDenied | The provided token does not have permission to view the provider information for the given user. |
| CannotReplaceProviderInfoForPrincipalInProtectedRealm | Provider information for Principals in this Realm cannot be replaced. |
| UserDeleted | The user is deleted. |
| ReplaceUserProviderInfoPermissionDenied | Could not replace the UserProviderInfo. |
| UserNotFound | The given User could not be found. |
| UserProviderInfoNotFound | The given UserProviderInfo could not be found. |
