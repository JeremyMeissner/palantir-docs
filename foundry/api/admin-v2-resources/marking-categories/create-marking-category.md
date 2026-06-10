---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/marking-categories/create-marking-category/"
title: "Create Marking Category \u2022 API Reference"
---
# Create Marking Category

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Creates a new MarkingCategory.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.createMarkingCategory

**path:** /api/v2/admin/markingCategories

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

**name:** CreateMarkingCategoryRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| initialPermissions | objectType | True | The initial permissions for the Marking Category. This can be changed later through MarkingCategoryPermission operations. The provided permissions must include at least one ADMINISTER role assignment.  WARNING: If you do not list your own principal ID or the ID of a Group that you are a member of as an ADMINISTER, you will create a Marking Category that you cannot administer. |
| name | stringType | True |  |
| description | stringType | True |  |

**example:** {"name":"Customer Data","description":"Markings related to data about our customers","initialPermissions":{"organizationRids":["ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa"],"roles":[{"role":"ADMINISTER","principalId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de"}],"isPublic":false}}

### Response

#### Body

The created MarkingCategory

**name:** MarkingCategory

**example:** {"categoryType":"CONJUNCTIVE","markings":["18212f9a-0e63-4b79-96a0-aae04df23336"],"createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","name":"Customer Data","description":"Markings related to data about our customers","createdTime":"2003-05-06T12:34:56.789Z","id":"0950264e-01c8-4e83-81a9-1a6b7f77621a","markingType":"MANDATORY"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| id | stringType | True | The ID of a marking category. For user-created categories, this will be a UUID. Markings associated with Organizations are placed in a category with ID "Organization". |
| name | stringType | True |  |
| description | stringType | True |  |
| categoryType | enumType | True |  |
| markingType | enumType | True |  |
| markings | listType | False |  |
| createdTime | stringType | True | The time at which the resource was created. |
| createdBy | stringType | False | The Foundry user who created this resource |

**example:** {"categoryType":"CONJUNCTIVE","markings":["18212f9a-0e63-4b79-96a0-aae04df23336"],"createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","name":"Customer Data","description":"Markings related to data about our customers","createdTime":"2003-05-06T12:34:56.789Z","id":"0950264e-01c8-4e83-81a9-1a6b7f77621a","markingType":"MANDATORY"}

### Error Responses

| name | description |
| --- | --- |
| CreateMarkingCategoryMissingInitialAdminRole | At least one ADMINISTER role assignment must be provided when creating a marking category. |
| CreateMarkingCategoryMissingOrganization | At least one organization must be provided when creating a marking category. |
| PrincipalNotFound | A principal (User or Group) with the given PrincipalId could not be found |
| CreateMarkingCategoryPermissionDenied | Could not create the MarkingCategory. |
