---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/marking-members/add-marking-members/"
title: "Add Marking Members \u2022 API Reference"
---
# Add Marking Members

## Endpoint

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.addMarkingMembers

**path:** /api/v2/admin/markings/{markingId}/markingMembers/add

### Operation Type

### Scopes

| name |
| --- |
| api:admin-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| markingId | stringType | True | The ID of a security marking. |

### Request

#### Body

**name:** AddMarkingMembersRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| principalIds | listType | False |  |

**example:** {"principalIds":["f05f8da4-b84c-4fca-9c77-8af0b13d11de"]}

### Error Responses

| name | description |
| --- | --- |
| PrincipalNotFound | A principal (User or Group) with the given PrincipalId could not be found |
| GetMarkingPermissionDenied | The provided token does not have permission to view the marking. |
| AddMarkingMembersPermissionDenied | Could not add the MarkingMember. |
| MarkingNotFound | The given Marking could not be found. |
