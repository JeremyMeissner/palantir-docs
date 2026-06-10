---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/users/get-users-batch/"
title: "Get Users Batch \u2022 API Reference"
---
# Get Users Batch

## Endpoint

Execute multiple get requests on User.

The maximum batch size for this endpoint is 500.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.getUsersBatch

**path:** /api/v2/admin/users/getBatch

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
| GetUsersBatchRequestElement | objectType | True |  |

**example:** [{"userId":"0d1fe74e-2b70-4a93-9b1a-80070637788b","status":"ACTIVE"}]

### Response

#### Body

**name:** GetUsersBatchResponse

**example:** {"data":{"0d1fe74e-2b70-4a93-9b1a-80070637788b":{"givenName":"John","familyName":"Smith","organization":"ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa","realm":"palantir-internal-realm","attributes":{"multipass:givenName":["John"],"multipass:familyName":["Smith"],"multipass:email:primary":["jsmith@example.com"],"multipass:realm":["eab0a251-ca1a-4a84-a482-200edfb8026f"],"multipass:organization-rid":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"department":["Finance"],"jobTitle":["Accountant"]},"id":"0d1fe74e-2b70-4a93-9b1a-80070637788b","email":"jsmith@example.com","username":"jsmith","status":"ACTIVE"}}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | mapType | False |  |

**example:** {"data":{"0d1fe74e-2b70-4a93-9b1a-80070637788b":{"givenName":"John","familyName":"Smith","organization":"ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa","realm":"palantir-internal-realm","attributes":{"multipass:givenName":["John"],"multipass:familyName":["Smith"],"multipass:email:primary":["jsmith@example.com"],"multipass:realm":["eab0a251-ca1a-4a84-a482-200edfb8026f"],"multipass:organization-rid":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"department":["Finance"],"jobTitle":["Accountant"]},"id":"0d1fe74e-2b70-4a93-9b1a-80070637788b","email":"jsmith@example.com","username":"jsmith","status":"ACTIVE"}}}
