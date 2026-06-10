---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/groups/get-groups-batch/"
title: "Get Groups Batch \u2022 API Reference"
---
# Get Groups Batch

## Endpoint

Execute multiple get requests on Group.

The maximum batch size for this endpoint is 500.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.getGroupsBatch

**path:** /api/v2/admin/groups/getBatch

### Operation Type

### Scopes

| name |
| --- |
| api:admin-read |

### Request

#### Body

**name:** body

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| GetGroupsBatchRequestElement | objectType | True |  |

**example:** [{"groupId":"0d1fe74e-2b70-4a93-9b1a-80070637788b"}]

### Response

#### Body

**name:** GetGroupsBatchResponse

**example:** {"data":{"0d1fe74e-2b70-4a93-9b1a-80070637788b":{"name":"Data Source Admins","organizations":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"description":"Create and modify data sources in the platform","realm":"palantir-internal-realm","attributes":{"multipass:realm":["eab0a251-ca1a-4a84-a482-200edfb8026f"],"multipass:organization-rid":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"]},"id":"0d1fe74e-2b70-4a93-9b1a-80070637788b"}}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | mapType | False |  |

**example:** {"data":{"0d1fe74e-2b70-4a93-9b1a-80070637788b":{"name":"Data Source Admins","organizations":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"description":"Create and modify data sources in the platform","realm":"palantir-internal-realm","attributes":{"multipass:realm":["eab0a251-ca1a-4a84-a482-200edfb8026f"],"multipass:organization-rid":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"]},"id":"0d1fe74e-2b70-4a93-9b1a-80070637788b"}}}
