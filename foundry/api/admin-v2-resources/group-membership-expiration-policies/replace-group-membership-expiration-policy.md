---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/group-membership-expiration-policies/replace-group-membership-expiration-policy/"
title: "Replace Group Membership Expiration Policy \u2022 API Reference"
---
# Replace Group Membership Expiration Policy

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Replace the GroupMembershipExpirationPolicy.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.replaceGroupMembershipExpirationPolicy

**path:** /api/v2/admin/groups/{groupId}/membershipExpirationPolicy

### Operation Type

### Scopes

| name |
| --- |
| api:admin-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| groupId | stringType | True | A Foundry Group ID. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** ReplaceGroupMembershipExpirationPolicyRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| maximumDuration | stringType | False | Members in this group must be added with expirations that are less than this duration in seconds into the future from the time they are added. |
| maximumValue | stringType | False | Members in this group must be added with expiration times that occur before this value. |

**example:** {"maximumDuration":30,"maximumValue":"2026-01-31T00:00:00.000Z"}

### Response

#### Body

The replaced GroupMembershipExpirationPolicy

**name:** GroupMembershipExpirationPolicy

**example:** {"maximumDuration":30,"maximumValue":"2026-01-31T00:00:00.000Z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| maximumValue | stringType | False | Members in this group must be added with expiration times that occur before this value. |
| maximumDuration | stringType | False | Members in this group must be added with expirations that are less than this duration in seconds into the future from the time they are added. |

**example:** {"maximumDuration":30,"maximumValue":"2026-01-31T00:00:00.000Z"}

### Error Responses

| name | description |
| --- | --- |
| ReplaceGroupMembershipExpirationPolicyPermissionDenied | Could not replace the GroupMembershipExpirationPolicy. |
| GroupNotFound | The given Group could not be found. |
