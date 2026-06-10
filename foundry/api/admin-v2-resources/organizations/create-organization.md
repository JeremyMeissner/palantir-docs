---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/organizations/create-organization/"
title: "Create Organization \u2022 API Reference"
---
# Create Organization

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Creates a new Organization.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.createOrganization

**path:** /api/v2/admin/organizations

### Operation Type

### Scopes

| name |
| --- |
| api:admin-write |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** CreateOrganizationRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| administrators | listType | False | The initial administrators of the Organization. At least one principal must be provided. |
| enrollmentRid | stringType | True | The RID of the Enrollment that this Organization belongs to. This must be provided. |
| name | stringType | True |  |
| host | stringType | False | The primary host name of the Organization. This should be used when constructing URLs for users of this Organization. |
| description | stringType | False |  |

**example:** {"enrollmentRid":"ri.control-panel.main.customer.466f812b-f974-4478-9d4f-90402cd3def6","name":"Example Organization","host":"example.palantirfoundry.com","administrators":["f05f8da4-b84c-4fca-9c77-8af0b13d11de"]}

### Response

#### Body

The created Organization

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
| CreateOrganizationMissingInitialAdminRole | At least one organization:administrator role grant must be provided when creating a organization. |
| OrganizationNameAlreadyExists | An organization with the same name already exists. |
| PrincipalNotFound | A principal (User or Group) with the given PrincipalId could not be found |
| CreateOrganizationPermissionDenied | Could not create the Organization. |
| EnrollmentNotFound | The given Enrollment could not be found. |
| OrganizationNotFound | The given Organization could not be found. |
