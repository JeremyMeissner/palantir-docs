---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/actions/apply-action-batch/"
title: "Apply Action Batch \u2022 API Reference"
---
# Apply Action Batch

## Endpoint

Applies multiple actions (of the same Action Type) using the given parameters.

Changes to objects or links stored in Object Storage V1 are eventually consistent and may take some time to be visible.
Edits to objects or links in Object Storage V2 will be visible immediately after the action completes.

Up to 20 actions may be applied in one call. Actions that only modify objects in Object Storage v2 and do not
call Functions may receive a higher limit.

Note that [notifications](/docs/foundry/action-types/notifications/) are not currently supported by this endpoint.

Third-party applications using this endpoint via OAuth2 must request the following operation scopes: `api:ontologies-read api:ontologies-write`.

**operationId:** v2.applyActionBatchV2

**path:** /api/v2/ontologies/{ontology}/actions/{action}/applyBatch

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |
| api:ontologies-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontology | stringType | True | The API name or RID of the Ontology. To find the API name or RID, use the **List Ontologies** endpoint or check the **Ontology Manager**. |
| action | stringType | True | The API name of the action to apply. To find the API name for your action, use the **List action types** endpoint or check the **Ontology Manager**. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| sdkPackageRid | stringType | False | The package rid of the generated SDK. |
| sdkVersion | stringType | False | The version of the generated SDK. |
| branch | stringType | False | The Foundry branch to apply the action against. If not specified, the default branch is used. Branches are an experimental feature and not all workflows are supported. |

### Request

#### Body

**name:** BatchApplyActionRequestV2

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| options | objectType | False |  |
| requests | listType | False |  |

**example:** {"requests":[{"parameters":{"id":80060,"newName":"Anna Smith-Doe"}},{"parameters":{"id":80061,"newName":"Joe Bloggs"}}]}

### Response

#### Body

Success response.

**name:** BatchApplyActionResponseV2

**example:** {}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| edits | unionType | False |  |

**example:** {}
