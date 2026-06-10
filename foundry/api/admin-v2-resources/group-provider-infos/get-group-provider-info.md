---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/group-provider-infos/get-group-provider-info/"
title: "Get Group Provider Info \u2022 API Reference"
---
# Get Group Provider Info

## Endpoint

Get the GroupProviderInfo.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.getGroupProviderInfo

**path:** /api/v2/admin/groups/{groupId}/providerInfo

### Operation Type

### Scopes

| name |
| --- |
| api:admin-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| groupId | stringType | True | A Foundry Group ID. |

### Response

#### Body

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
| GroupProviderInfoNotFound | The given GroupProviderInfo could not be found. |
| GroupNotFound | The given Group could not be found. |
