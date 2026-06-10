---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/group-members/add-group-members/"
title: "Add Group Members \u2022 API Reference"
---
# Add Group Members

## Endpoint

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.addGroupMembers

**path:** /api/v2/admin/groups/{groupId}/groupMembers/add

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

**name:** AddGroupMembersRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| principalIds | listType | False |  |
| expiration | stringType | False |  |

**example:** {"expiration":"2026-01-31T00:00:00.000Z","principalIds":["f05f8da4-b84c-4fca-9c77-8af0b13d11de"]}

### Error Responses

| name | description |
| --- | --- |
| PrincipalNotFound | A principal (User or Group) with the given PrincipalId could not be found |
| InvalidGroupMembershipExpiration | The member expiration you provided does not conform to the Group's requirements for member expirations. |
| AddGroupMembersPermissionDenied | Could not add the GroupMember. |
| GroupNotFound | The given Group could not be found. |
