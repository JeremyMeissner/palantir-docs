---
source_url: "https://www.palantir.com/docs/foundry/api/checkpoints-v2-resources/records/get-record/"
title: "Get Record \u2022 API Reference"
---
# Get Record

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Retrieve a single checkpoint record by id.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:checkpoints-read`.

**operationId:** v2.getRecord

**path:** /api/v2/checkpoints/records/{recordRid}

### Operation Type

### Scopes

| name |
| --- |
| api:checkpoints-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| recordRid | stringType | True | Identifier of a checkpoint record. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** Record

**example:** {"projectRid":"ri.compass.main.folder.d4e5f6a7-b8c9-0123-defa-234567890123","delegateUserId":"0d1fe74e-2b70-4a93-9b1a-80070637788b","configRid":"ri.checkpoints.main.config.b2c3d4e5-f6a7-8901-bcde-f12345678901","organizationRid":"ri.multipass..organization.e5f6a7b8-c9d0-1234-efab-345678901234","checkpointedItems":[{"type":"checkpointedResource","rid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","resourceType":"DATASET","compassPath":{"value":"/My Project/My Dataset"},"orgMarkings":[]}],"rid":"ri.checkpoints.main.checkpoint.a1b2c3d4-e5f6-7890-abcd-ef1234567890","type":"CONTOUR_EXPORT","actingUser":{"userId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","username":{"value":"admin"}},"createdAt":"2023-11-14T09:30:00.000Z","approvalsMetadata":{"approvalsTaskId":"e3f4a5b6-c7d8-9012-efab-123456789012","approvalsSubtaskIds":["f4a5b6c7-d8e9-0123-fabc-234567890123"]},"scope":"USER_SCOPED","interactionRid":"ri.checkpoints.main.checkpointable-interaction.c3d4e5f6-a7b8-9012-cdef-123456789012","namespaceRid":"ri.compass.main.folder.f6a7b8c9-d0e1-2345-fabc-456789012345","justification":{"type":"acknowledgementJustification","prompt":"I acknowledge this action","title":"Export Confirmation"}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | Identifier of a checkpoint record. |
| configRid | stringType | False | Identifier of the checkpoint configuration that produced a record. |
| type | enumType | True | Checkpoint type identifier. See the [Checkpoints documentation](/docs/foundry/checkpoints/overview) for more details. |
| scope | enumType | True | Indicates whether the checkpoint was scoped to a user or resource. |
| actingUser | objectType | True | User that performed the checkpoint action. |
| delegateUserId | stringType | False | A Foundry User ID. |
| createdAt | stringType | True | The time at which the checkpoint record was created. |
| checkpointedItems | listType | False |  |
| justification | unionType | True | Justification submitted by the user to pass a checkpoint. |
| projectRid | stringType | False | Identifier of the project that scoped a checkpoint. |
| organizationRid | stringType | False | Identifier of the organization associated with a checkpoint. |
| namespaceRid | stringType | False | Identifier of the namespace associated with a checkpoint. |
| interactionRid | stringType | False | Identifier of the interaction associated with a record. |
| approvalsMetadata | objectType | False | Metadata linking a checkpoint record to an Approvals workflow. |

**example:** {"projectRid":"ri.compass.main.folder.d4e5f6a7-b8c9-0123-defa-234567890123","delegateUserId":"0d1fe74e-2b70-4a93-9b1a-80070637788b","configRid":"ri.checkpoints.main.config.b2c3d4e5-f6a7-8901-bcde-f12345678901","organizationRid":"ri.multipass..organization.e5f6a7b8-c9d0-1234-efab-345678901234","checkpointedItems":[{"type":"checkpointedResource","rid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","resourceType":"DATASET","compassPath":{"value":"/My Project/My Dataset"},"orgMarkings":[]}],"rid":"ri.checkpoints.main.checkpoint.a1b2c3d4-e5f6-7890-abcd-ef1234567890","type":"CONTOUR_EXPORT","actingUser":{"userId":"f05f8da4-b84c-4fca-9c77-8af0b13d11de","username":{"value":"admin"}},"createdAt":"2023-11-14T09:30:00.000Z","approvalsMetadata":{"approvalsTaskId":"e3f4a5b6-c7d8-9012-efab-123456789012","approvalsSubtaskIds":["f4a5b6c7-d8e9-0123-fabc-234567890123"]},"scope":"USER_SCOPED","interactionRid":"ri.checkpoints.main.checkpointable-interaction.c3d4e5f6-a7b8-9012-cdef-123456789012","namespaceRid":"ri.compass.main.folder.f6a7b8c9-d0e1-2345-fabc-456789012345","justification":{"type":"acknowledgementJustification","prompt":"I acknowledge this action","title":"Export Confirmation"}}

### Error Responses

| name | description |
| --- | --- |
| CheckpointRecordNotFound | The checkpoint record could not be found. |
| CheckpointRecordPermissionDenied | The caller does not have permission to access the checkpoint record. |
| RecordNotFound | The given Record could not be found. |
