---
source_url: "https://www.palantir.com/docs/foundry/api/checkpoints-v2-resources/records/get-records-batch/"
title: "Get Records Batch \u2022 API Reference"
---
# Get Records Batch

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Fetch multiple checkpoint records in a single request. Records not found
or inaccessible to the user will be omitted from the response.

The maximum batch size for this endpoint is 100.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:checkpoints-read`.

**operationId:** v2.getRecordsBatch

**path:** /api/v2/checkpoints/records/getBatch

### Operation Type

### Scopes

| name |
| --- |
| api:checkpoints-read |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** body

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| GetRecordsBatchRequestElement | objectType | True |  |

**example:** [{"recordRid":"ri.checkpoints.main.checkpoint.a1b2c3d4-e5f6-7890-abcd-ef1234567890"}]

### Response

#### Body

**name:** GetRecordsBatchResponse

**example:** {"data":{"ri.checkpoints.main.checkpoint.a1b2c3d4-e5f6-7890-abcd-ef1234567890":{"projectRid":"ri.compass.main.folder.d4e5f6a7-b8c9-0123-defa-234567890123","delegateUserId":"0d1fe74e-2b70-4a93-9b1a-80070637788b","configRid":"ri.checkpoints.main.config.b2c3d4e5-f6a7-8901-bcde-f12345678901","organizationRid":"ri.multipass..organization.e5f6a7b8-c9d0-1234-efab-345678901234","checkpointedItems":[{"type":"checkpointedResource","rid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","resourceType":"DATASET","compassPath":{"value":"/My Project/My Dataset"},"orgMarkings":[]}],"rid":"ri.checkpoints.main.checkpoint.a1b2c3d4-e5f6-7890-abcd-ef1234567890","type":"CONTOUR_EXPORT","actingUser":{"userId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","username":{"value":"admin"}},"createdAt":"2023-11-14T09:30:00.000Z","approvalsMetadata":{"approvalsTaskId":"e3f4a5b6-c7d8-9012-efab-123456789012","approvalsSubtaskIds":["f4a5b6c7-d8e9-0123-fabc-234567890123"]},"scope":"USER_SCOPED","interactionRid":"ri.checkpoints.main.checkpointable-interaction.c3d4e5f6-a7b8-9012-cdef-123456789012","namespaceRid":"ri.compass.main.folder.f6a7b8c9-d0e1-2345-fabc-456789012345","justification":{"type":"acknowledgementJustification","prompt":"I acknowledge this action","title":"Export Confirmation"}}}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | mapType | False |  |

**example:** {"data":{"ri.checkpoints.main.checkpoint.a1b2c3d4-e5f6-7890-abcd-ef1234567890":{"projectRid":"ri.compass.main.folder.d4e5f6a7-b8c9-0123-defa-234567890123","delegateUserId":"0d1fe74e-2b70-4a93-9b1a-80070637788b","configRid":"ri.checkpoints.main.config.b2c3d4e5-f6a7-8901-bcde-f12345678901","organizationRid":"ri.multipass..organization.e5f6a7b8-c9d0-1234-efab-345678901234","checkpointedItems":[{"type":"checkpointedResource","rid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","resourceType":"DATASET","compassPath":{"value":"/My Project/My Dataset"},"orgMarkings":[]}],"rid":"ri.checkpoints.main.checkpoint.a1b2c3d4-e5f6-7890-abcd-ef1234567890","type":"CONTOUR_EXPORT","actingUser":{"userId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","username":{"value":"admin"}},"createdAt":"2023-11-14T09:30:00.000Z","approvalsMetadata":{"approvalsTaskId":"e3f4a5b6-c7d8-9012-efab-123456789012","approvalsSubtaskIds":["f4a5b6c7-d8e9-0123-fabc-234567890123"]},"scope":"USER_SCOPED","interactionRid":"ri.checkpoints.main.checkpointable-interaction.c3d4e5f6-a7b8-9012-cdef-123456789012","namespaceRid":"ri.compass.main.folder.f6a7b8c9-d0e1-2345-fabc-456789012345","justification":{"type":"acknowledgementJustification","prompt":"I acknowledge this action","title":"Export Confirmation"}}}}
