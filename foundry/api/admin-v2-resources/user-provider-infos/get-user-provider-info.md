---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/user-provider-infos/get-user-provider-info/"
title: "Get User Provider Info \u2022 API Reference"
---
# Get User Provider Info

## Endpoint

Get the UserProviderInfo.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.getUserProviderInfo

**path:** /api/v2/admin/users/{userId}/providerInfo

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
| UserDeleted | The user is deleted. |
| UserProviderInfoNotFound | The given UserProviderInfo could not be found. |
| UserNotFound | The given User could not be found. |
