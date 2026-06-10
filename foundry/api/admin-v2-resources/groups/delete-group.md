---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/groups/delete-group/"
title: "Delete Group \u2022 API Reference"
---
# Delete Group

## Endpoint

Delete the Group with the specified id.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.deleteGroup

**path:** /api/v2/admin/groups/{groupId}

### Operation Type

### Scopes

| name |
| --- |
| api:admin-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| groupId | stringType | True | A Foundry Group ID. |

### Error Responses

| name | description |
| --- | --- |
| DeleteGroupPermissionDenied | Could not delete the Group. |
| GroupNotFound | The given Group could not be found. |
