---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/markings/replace-marking/"
title: "Replace Marking \u2022 API Reference"
---
# Replace Marking

## Endpoint

Replace the Marking with the specified id.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-write`.

**operationId:** v2.replaceMarking

**path:** /api/v2/admin/markings/{markingId}

### Operation Type

### Scopes

| name |
| --- |
| api:admin-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| markingId | stringType | True | The ID of a security marking. |

### Request

#### Body

**name:** ReplaceMarkingRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| name | stringType | True |  |
| description | stringType | False |  |

**example:** {"name":"PII","description":"Contains personally identifiable information about our customers"}

### Response

#### Body

The replaced Marking

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
| MarkingNameInCategoryAlreadyExists | A marking with the same name already exists in the category. |
| GetMarkingPermissionDenied | The provided token does not have permission to view the marking. |
| MarkingNameIsEmpty | The marking name is empty. |
| ReplaceMarkingPermissionDenied | Could not replace the Marking. |
| MarkingNotFound | The given Marking could not be found. |
