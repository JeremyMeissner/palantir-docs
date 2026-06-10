---
source_url: "https://www.palantir.com/docs/foundry/api/ontology-resources/actions/apply-action-batch/"
title: "Apply Action Batch \u2022 API Reference"
---
# Apply Action Batch

## Endpoint

Applies multiple actions (of the same Action Type) using the given parameters.
Changes to objects or links stored in Object Storage V1 are eventually consistent and may take some time to be visible.
Edits to objects or links in Object Storage V2 will be visible immediately after the action completes.

Up to 20 actions may be applied in one call. Actions that only modify objects in Object Storage v2 and do not
call Functions may receive a higher limit.

Note that [parameter default values](/docs/foundry/action-types/parameters-default-value/) and
[notifications](/docs/foundry/action-types/notifications/) are not currently supported by this endpoint.

Third-party applications using this endpoint via OAuth2 must request the following operation scopes: `api:ontologies-read api:ontologies-write`.

**operationId:** v1.applyActionBatch

**path:** /api/v1/ontologies/{ontologyRid}/actions/{actionType}/applyBatch

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |
| api:ontologies-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontologyRid | stringType | True | The unique Resource Identifier (RID) of the Ontology that contains the action. To look up your Ontology RID, please use the **List ontologies** endpoint or check the **Ontology Manager**. |
| actionType | stringType | True | The API name of the action to apply. To find the API name for your action, use the **List action types** endpoint or check the **Ontology Manager**. |

### Request

#### Body

**name:** BatchApplyActionRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| requests | listType | False |  |

**example:** {"requests":[{"parameters":{"id":80060,"newName":"Anna Smith-Doe"}},{"parameters":{"id":80061,"newName":"Joe Bloggs"}}]}

### Response

#### Body

Success response.

**name:** BatchApplyActionResponse

**example:** {}

**example:** {}
