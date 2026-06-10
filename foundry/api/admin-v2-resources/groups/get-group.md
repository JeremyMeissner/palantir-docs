---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/groups/get-group/"
title: "Get Group \u2022 API Reference"
---
# Get Group

## Endpoint

Get the Group with the specified id.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.getGroup

**path:** /api/v2/admin/groups/{groupId}

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

**name:** Group

**example:** {"name":"Data Source Admins","organizations":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"description":"Create and modify data sources in the platform","realm":"palantir-internal-realm","attributes":{"multipass:realm":["eab0a251-ca1a-4a84-a482-200edfb8026f"],"multipass:organization-rid":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"]},"id":"0d1fe74e-2b70-4a93-9b1a-80070637788b"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| id | stringType | True | A Foundry Group ID. |
| name | stringType | True | The name of the Group. |
| description | stringType | False | A description of the Group. |
| realm | stringType | True | Identifies which Realm a User or Group is a member of. The `palantir-internal-realm` is used for Users or Groups that are created in Foundry by administrators and not associated with any SSO provider. |
| organizations | listType | False | The RIDs of the Organizations whose members can see this group. At least one Organization RID must be listed. |
| attributes | mapType | False | A map of the Group's attributes. Attributes prefixed with "multipass:" are reserved for internal use by Foundry and are subject to change. |

**example:** {"name":"Data Source Admins","organizations":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"description":"Create and modify data sources in the platform","realm":"palantir-internal-realm","attributes":{"multipass:realm":["eab0a251-ca1a-4a84-a482-200edfb8026f"],"multipass:organization-rid":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"]},"id":"0d1fe74e-2b70-4a93-9b1a-80070637788b"}

### Error Responses

| name | description |
| --- | --- |
| GroupNotFound | The given Group could not be found. |
