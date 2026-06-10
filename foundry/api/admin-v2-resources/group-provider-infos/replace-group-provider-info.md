---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/group-provider-infos/replace-group-provider-info/"
title: "Replace Group Provider Info \u2022 API Reference"
---
# Replace Group Provider Info

## Endpoint

Replace the GroupProviderInfo.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.replaceGroupProviderInfo

**path:** /api/v2/admin/groups/{groupId}/providerInfo

### Operation Type

### Scopes

| name |
| --- |
| api:admin-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| groupId | stringType | True | A Foundry Group ID. |

### Request

#### Body

**name:** ReplaceGroupProviderInfoRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| providerId | stringType | True | The ID of the Group in the external authentication provider. This value is determined by the authentication provider. At most one Group can have a given provider ID in a given Realm. |

**example:** {"providerId":"2838c8f3-d76a-4e99-acf1-1dee537e4c48"}

### Response

#### Body

The replaced GroupProviderInfo

**name:** GroupProviderInfo

**example:** {"providerId":"2838c8f3-d76a-4e99-acf1-1dee537e4c48"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| providerId | stringType | True | The ID of the Group in the external authentication provider. This value is determined by the authentication provider. At most one Group can have a given provider ID in a given Realm. |

**example:** {"providerId":"2838c8f3-d76a-4e99-acf1-1dee537e4c48"}

### Error Responses

| name | description |
| --- | --- |
| GetGroupProviderInfoPermissionDenied | The provided token does not have permission to view the provider information for the given group. |
| CannotReplaceProviderInfoForPrincipalInProtectedRealm | Provider information for Principals in this Realm cannot be replaced. |
| ReplaceGroupProviderInfoPermissionDenied | Could not replace the GroupProviderInfo. |
| GroupNotFound | The given Group could not be found. |
| GroupProviderInfoNotFound | The given GroupProviderInfo could not be found. |
