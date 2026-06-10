---
source_url: "https://www.palantir.com/docs/foundry/api/ontology-resources/actions/apply-action/"
title: "Apply Action \u2022 API Reference"
---
# Apply Action

## Endpoint

Applies an action using the given parameters.

Changes to objects or links stored in Object Storage V1 are eventually consistent and may take some time to be visible.
Edits to objects or links in Object Storage V2 will be visible immediately after the action completes.

Note that [parameter default values](/docs/foundry/action-types/parameters-default-value/) are not currently supported by
this endpoint.

Third-party applications using this endpoint via OAuth2 must request the following operation scopes: `api:ontologies-read api:ontologies-write`.

**operationId:** v1.applyAction

**path:** /api/v1/ontologies/{ontologyRid}/actions/{actionType}/apply

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

**name:** ApplyActionRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| parameters | mapType | False |  |

**example:** {"parameters":{"id":80060,"newName":"Anna Smith-Doe"}}

### Response

#### Body

Success response.

**name:** ApplyActionResponse

**example:** {}

**example:** {}
