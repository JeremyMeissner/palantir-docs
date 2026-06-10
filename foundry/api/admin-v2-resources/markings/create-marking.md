---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/markings/create-marking/"
title: "Create Marking \u2022 API Reference"
---
# Create Marking

## Endpoint

Creates a new Marking.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.createMarking

**path:** /api/v2/admin/markings

### Operation Type

### Scopes

| name |
| --- |
| api:admin-write |

### Request

#### Body

**name:** CreateMarkingRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| initialRoleAssignments | listType | False | The initial roles that will be assigned when the Marking is created. At least one ADMINISTER role must be provided. This can be changed later through the MarkingRoleAssignment operations.  WARNING: If you do not include your own principal ID or the ID of a Group that you are a member of, you will create a Marking that you cannot administer. |
| initialMembers | listType | False | Users and Groups that will be able to view resources protected by this Marking. This can be changed later through the MarkingMember operations. |
| name | stringType | True |  |
| description | stringType | False |  |
| categoryId | stringType | True | The ID of a marking category. For user-created categories, this will be a UUID. Markings associated with Organizations are placed in a category with ID "Organization". |

**example:** {"initialMembers":["f05f8da4-b84c-4fca-9c77-8af0b13d11de"],"name":"PII","description":"Contains personally identifiable information about our customers","categoryId":"0950264e-01c8-4e83-81a9-1a6b7f77621a","initialRoleAssignments":[{"role":"ADMINISTER","principalId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de"}]}

### Response

#### Body

The created Marking

**name:** Marking

**example:** {"createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","organization":"ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa","name":"PII","description":"Contains personally identifiable information about our customers","createdTime":"2003-05-06T12:34:56.789Z","id":"18212f9a-0e63-4b79-96a0-aae04df23336","categoryId":"0950264e-01c8-4e83-81a9-1a6b7f77621a"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| id | stringType | True | The ID of a security marking. |
| categoryId | stringType | True | The ID of a marking category. For user-created categories, this will be a UUID. Markings associated with Organizations are placed in a category with ID "Organization". |
| name | stringType | True |  |
| description | stringType | False |  |
| organization | stringType | False | If this marking is associated with an Organization, its RID will be populated here. |
| createdTime | stringType | True | The time at which the resource was created. |
| createdBy | stringType | False | The Foundry user who created this resource |

**example:** {"createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","organization":"ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa","name":"PII","description":"Contains personally identifiable information about our customers","createdTime":"2003-05-06T12:34:56.789Z","id":"18212f9a-0e63-4b79-96a0-aae04df23336","categoryId":"0950264e-01c8-4e83-81a9-1a6b7f77621a"}

### Error Responses

| name | description |
| --- | --- |
| GetMarkingCategoryPermissionDenied | The provided token does not have permission to view the marking category. |
| PrincipalNotFound | A principal (User or Group) with the given PrincipalId could not be found |
| CreateMarkingMissingInitialAdminRole | At least one ADMINISTER role assignment must be provided when creating a marking. |
| MarkingNameInCategoryAlreadyExists | A marking with the same name already exists in the category. |
| MarkingNameIsEmpty | The marking name is empty. |
| CreateMarkingPermissionDenied | Could not create the Marking. |
| MarkingCategoryNotFound | The given MarkingCategory could not be found. |
