---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/organizations/list-available-roles-organization/"
title: "List Available Roles Organization \u2022 API Reference"
---
# List Available Roles Organization

## Endpoint

List all roles that can be assigned to a principal for the given Organization.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.listAvailableRolesOrganization

**path:** /api/v2/admin/organizations/{organizationRid}/listAvailableRoles

### Operation Type

### Scopes

| name |
| --- |
| api:admin-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| organizationRid | stringType | True |  |

### Response

#### Body

**name:** ListAvailableOrganizationRolesResponse

**example:** {"data":[{"roleSetId":"3181190f-f6b8-4649-90ec-64fa2d847204","operations":["compass:read-resource"],"id":"8bf49052-dc37-4528-8bf0-b551cfb71268","type":"ORGANIZATION"}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |

**example:** {"data":[{"roleSetId":"3181190f-f6b8-4649-90ec-64fa2d847204","operations":["compass:read-resource"],"id":"8bf49052-dc37-4528-8bf0-b551cfb71268","type":"ORGANIZATION"}]}

### Error Responses

| name | description |
| --- | --- |
| ListAvailableRolesOrganizationPermissionDenied | Could not listAvailableRoles the Organization. |
| OrganizationNotFound | The given Organization could not be found. |
