---
source_url: "https://www.palantir.com/docs/foundry/api/admin-v2-resources/markings/get-markings-batch/"
title: "Get Markings Batch \u2022 API Reference"
---
# Get Markings Batch

## Endpoint

Execute multiple get requests on Marking.

The maximum batch size for this endpoint is 500.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:admin-read`.

**operationId:** v2.getMarkingsBatch

**path:** /api/v2/admin/markings/getBatch

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
| GetMarkingsBatchRequestElement | objectType | True |  |

**example:** [{"markingId":"18212f9a-0e63-4b79-96a0-aae04df23336"}]

### Response

#### Body

**name:** GetMarkingsBatchResponse

**example:** {"data":{"18212f9a-0e63-4b79-96a0-aae04df23336":{"createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","organization":"ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa","name":"PII","description":"Contains personally identifiable information about our customers","createdTime":"2003-05-06T12:34:56.789Z","id":"18212f9a-0e63-4b79-96a0-aae04df23336","categoryId":"0950264e-01c8-4e83-81a9-1a6b7f77621a"}}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | mapType | False |  |

**example:** {"data":{"18212f9a-0e63-4b79-96a0-aae04df23336":{"createdBy":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","organization":"ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa","name":"PII","description":"Contains personally identifiable information about our customers","createdTime":"2003-05-06T12:34:56.789Z","id":"18212f9a-0e63-4b79-96a0-aae04df23336","categoryId":"0950264e-01c8-4e83-81a9-1a6b7f77621a"}}}
