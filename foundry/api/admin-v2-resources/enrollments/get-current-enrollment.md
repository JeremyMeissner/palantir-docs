---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/enrollments/get-current-enrollment/"
title: "Get Current Enrollment \u2022 API Reference"
---
# Get Current Enrollment

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Returns the Enrollment associated with the current User's primary organization.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.getCurrentEnrollment

**path:** /api/v2/admin/enrollments/getCurrent

### Operation Type

### Scopes

| name |
| --- |
| api:admin-read |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** Enrollment

**example:** {"name":"Example Enrollment","createdTime":"2003-05-06T12:34:56.789Z","rid":"ri.control-panel.main.customer.466f812b-f974-4478-9d4f-90402cd3def6"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True |  |
| name | stringType | True |  |
| createdTime | stringType | False | The time at which the resource was created. |

**example:** {"name":"Example Enrollment","createdTime":"2003-05-06T12:34:56.789Z","rid":"ri.control-panel.main.customer.466f812b-f974-4478-9d4f-90402cd3def6"}

### Error Responses

| name | description |
| --- | --- |
| GetCurrentEnrollmentPermissionDenied | Could not getCurrent the Enrollment. |
| EnrollmentNotFound | The given Enrollment could not be found. |
