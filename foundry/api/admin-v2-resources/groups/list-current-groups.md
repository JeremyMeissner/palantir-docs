---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/groups/list-current-groups/"
title: "List Current Groups \u2022 API Reference"
---
# List Current Groups

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Returns all Groups which contain the current user as a direct or transitive member. For example if the current user is a member of Group A and Group A is a member of Group B, this endpoint will return Group A and Group B.

Unlike the list Group Memberships endpoint which requires the `api:admin-read` scope, this endpoint
does not require any particular scopes and can be used by any authenticated user to retrieve their own
group memberships.

**operationId:** v2.listCurrentGroups

**path:** /api/v2/admin/groups/listCurrent

### Operation Type

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** ListCurrentGroupsResponse

**example:** {"data":[{"name":"Data Source Admins","organizations":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"description":"Create and modify data sources in the platform","realm":"palantir-internal-realm","attributes":{"multipass:realm":["eab0a251-ca1a-4a84-a482-200edfb8026f"],"multipass:organization-rid":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"]},"id":"0d1fe74e-2b70-4a93-9b1a-80070637788b"}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |

**example:** {"data":[{"name":"Data Source Admins","organizations":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"description":"Create and modify data sources in the platform","realm":"palantir-internal-realm","attributes":{"multipass:realm":["eab0a251-ca1a-4a84-a482-200edfb8026f"],"multipass:organization-rid":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"]},"id":"0d1fe74e-2b70-4a93-9b1a-80070637788b"}]}

### Error Responses

| name | description |
| --- | --- |
| ListCurrentGroupsPermissionDenied | Could not listCurrent the Group. |
