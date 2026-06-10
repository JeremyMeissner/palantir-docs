---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/users/get-current-user/"
title: "Get Current User \u2022 API Reference"
---
# Get Current User

## Endpoint

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.getCurrentUser

**path:** /api/v2/admin/users/getCurrent

### Operation Type

### Scopes

| name |
| --- |
| api:admin-read |

### Response

#### Body

**name:** User

**example:** {"givenName":"John","familyName":"Smith","organization":"ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa","realm":"palantir-internal-realm","attributes":{"multipass:givenName":["John"],"multipass:familyName":["Smith"],"multipass:email:primary":["jsmith@example.com"],"multipass:realm":["eab0a251-ca1a-4a84-a482-200edfb8026f"],"multipass:organization-rid":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"department":["Finance"],"jobTitle":["Accountant"]},"id":"0d1fe74e-2b70-4a93-9b1a-80070637788b","email":"jsmith@example.com","username":"jsmith","status":"ACTIVE"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| id | stringType | True | A Foundry User ID. |
| username | stringType | True | The Foundry username of the User. This is unique within the realm. |
| givenName | stringType | False | The given name of the User. |
| familyName | stringType | False | The family name (last name) of the User. |
| email | stringType | False | The email at which to contact a User. Multiple users may have the same email address. |
| realm | stringType | True | Identifies which Realm a User or Group is a member of. The `palantir-internal-realm` is used for Users or Groups that are created in Foundry by administrators and not associated with any SSO provider. |
| organization | stringType | False | The RID of the user's primary Organization. This will be blank for third-party application service users. |
| status | enumType | True | The current status of the user. |
| attributes | mapType | False | A map of the User's attributes. Attributes prefixed with "multipass:" are reserved for internal use by Foundry and are subject to change. Additional attributes may be configured by Foundry administrators in  Control Panel and populated by the User's SSO provider upon login. |

**example:** {"givenName":"John","familyName":"Smith","organization":"ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa","realm":"palantir-internal-realm","attributes":{"multipass:givenName":["John"],"multipass:familyName":["Smith"],"multipass:email:primary":["jsmith@example.com"],"multipass:realm":["eab0a251-ca1a-4a84-a482-200edfb8026f"],"multipass:organization-rid":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"department":["Finance"],"jobTitle":["Accountant"]},"id":"0d1fe74e-2b70-4a93-9b1a-80070637788b","email":"jsmith@example.com","username":"jsmith","status":"ACTIVE"}

### Error Responses

| name | description |
| --- | --- |
| GetCurrentUserPermissionDenied | Could not getCurrent the User. |
