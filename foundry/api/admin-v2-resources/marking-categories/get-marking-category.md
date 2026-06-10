---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/marking-categories/get-marking-category/"
title: "Get Marking Category \u2022 API Reference"
---
# Get Marking Category

## Endpoint

Get the MarkingCategory with the specified id.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.getMarkingCategory

**path:** /api/v2/admin/markingCategories/{markingCategoryId}

### Operation Type

### Scopes

| name |
| --- |
| api:admin-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| markingCategoryId | stringType | True | The ID of a marking category. For user-created categories, this will be a UUID. Markings associated with Organizations are placed in a category with ID "Organization". |

### Response

#### Body

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
| GetMarkingCategoryPermissionDenied | The provided token does not have permission to view the marking category. |
| MarkingCategoryNotFound | The given MarkingCategory could not be found. |
