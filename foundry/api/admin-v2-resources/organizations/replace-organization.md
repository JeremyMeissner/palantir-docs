---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/organizations/replace-organization/"
title: "Replace Organization \u2022 API Reference"
---
# Replace Organization

## Endpoint

Replace the Organization with the specified rid.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.replaceOrganization

**path:** /api/v2/admin/organizations/{organizationRid}

### Operation Type

### Scopes

| name |
| --- |
| api:admin-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| organizationRid | stringType | True |  |

### Request

#### Body

**name:** ReplaceOrganizationRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| name | stringType | True |  |
| host | stringType | False | The primary host name of the Organization. This should be used when constructing URLs for users of this Organization. |
| description | stringType | False |  |

**example:** {"name":"Example Organization","host":"example.palantirfoundry.com"}

### Response

#### Body

The replaced Organization

**name:** Organization

**example:** {"name":"Example Organization","host":"example.palantirfoundry.com","rid":"ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa","markingId":"18212f9a-0e63-4b79-96a0-aae04df23336"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True |  |
| name | stringType | True |  |
| description | stringType | False |  |
| markingId | stringType | True | The ID of this Organization's underlying marking. Organization guest access can be managed by updating the membership of this Marking. |
| host | stringType | False | The primary host name of the Organization. This should be used when constructing URLs for users of this Organization. |

**example:** {"name":"Example Organization","host":"example.palantirfoundry.com","rid":"ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa","markingId":"18212f9a-0e63-4b79-96a0-aae04df23336"}

### Error Responses

| name | description |
| --- | --- |
| InvalidHostName | The provided hostname must be a valid domain name. The only allowed characters are letters, numbers, periods, and hyphens. |
| OrganizationNameAlreadyExists | An organization with the same name already exists. |
| ReplaceOrganizationPermissionDenied | Could not replace the Organization. |
| OrganizationNotFound | The given Organization could not be found. |
