---
source_url: "https://www.palantir.com/docs/gotham/api/revdb-resources/objects/list-linked-objects/"
title: "List linked objects \u2022 API Reference"
---
# List linked objects

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Lists the linked objects for a specific object and the given link type.

Invalid link type results in an [InvalidOntologyTypes error](/docs/gotham/api/general/overview/errors#objects-errors).

**operationId:** v1.listLinkedObjects

**path:** /api/gotham/v1/objects/{primaryKey}/links/{linkType}

### Operation Type

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| primaryKey | stringType | True | The primary key of the object from which the links originate. |
| linkType | stringType | True | The type of the link that exists between the object and the requested objects. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| pageSize | integerType | False | The maximum size of the page to return. The default is 1,000 and the maximum allowed is 1,000. If a page size greater than 1,000 is requested, then it will default to 1,000. The service may return fewer or more results than requested, but will always return at least one result per page as long as there are more results. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page request and populated from the `nextPageToken` field of the previous response in subsequent requests |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Response

#### Body

Success response

**name:** ListLinkedObjectsResponse

**example:** [{"primaryKey":"ri.gotham.111111-0.object-internal.222222","objectType":"com.palantir.object.person","properties":{"com.palantir.property.name":[{"FIRST_NAME":"Chris","LAST_NAME":"Smith"}],"com.palantir.property.age":[78]}},{"primaryKey":"ri.gotham.111111-0.object-internal.333333","objectType":"com.palantir.object.person","properties":{"com.palantir.property.name":[{"FIRST_NAME":"Mary","LAST_NAME":"Smith"}],"com.palantir.property.age":[79]}}]

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and populate the next request's `pageToken` field with it. |
| data | listType | False |  |

**example:** [{"primaryKey":"ri.gotham.111111-0.object-internal.222222","objectType":"com.palantir.object.person","properties":{"com.palantir.property.name":[{"FIRST_NAME":"Chris","LAST_NAME":"Smith"}],"com.palantir.property.age":[78]}},{"primaryKey":"ri.gotham.111111-0.object-internal.333333","objectType":"com.palantir.object.person","properties":{"com.palantir.property.name":[{"FIRST_NAME":"Mary","LAST_NAME":"Smith"}],"com.palantir.property.age":[79]}}]
