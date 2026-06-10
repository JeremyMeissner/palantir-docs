---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/group-members/remove-group-members/"
title: "Remove Group Members \u2022 API Reference"
---
# Remove Group Members

## Endpoint

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.removeGroupMembers

**path:** /api/v2/admin/groups/{groupId}/groupMembers/remove

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

**name:** RemoveGroupMembersRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| principalIds | listType | False |  |

**example:** {"principalIds":["f05f8da4-b84c-4fca-9c77-8af0b13d11de"]}

### Error Responses

| name | description |
| --- | --- |
| PrincipalNotFound | A principal (User or Group) with the given PrincipalId could not be found |
| RemoveGroupMembersPermissionDenied | Could not remove the GroupMember. |
| GroupNotFound | The given Group could not be found. |
