---
source_url: "https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/actions/apply-action/"
title: "Apply Action \u2022 API Reference"
---
# Apply Action

## Endpoint

Applies an action using the given parameters. 

Changes to objects or links stored in Object Storage V1 are eventually consistent and may take some time to be visible.
Edits to objects or links in Object Storage V2 will be visible immediately after the action completes.

Note that a 200 HTTP status code only indicates that the request was received and processed by the server. 
See the validation result in the response body to determine if the action was applied successfully.

Note that [parameter default values](/docs/foundry/action-types/parameters-default-value/) are not currently supported by
this endpoint.

Third-party applications using this endpoint via OAuth2 must request the following operation scopes: `api:ontologies-read api:ontologies-write`.

**operationId:** v2.applyActionV2

**path:** /api/v2/ontologies/{ontology}/actions/{action}/apply

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
| transactionId | stringType | False | The ID of an Ontology transaction to apply the action against. Transactions are an experimental feature and all workflows may not be supported. |
| scenarioRid | stringType | False | The resource identifier of an ontology scenario to apply the action against. |
| branch | stringType | False | The Foundry branch to apply the action against. If not specified, the default branch is used. Branches are an experimental feature and not all workflows are supported. |

### Request

#### Body

**name:** ApplyActionRequestV2

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| options | objectType | False |  |
| parameters | mapType | False |  |

**example:** {"parameters":{"id":80060,"newName":"Anna Smith-Doe"}}

### Response

#### Body

Success response.

**name:** SyncApplyActionResponseV2

**example:** {"operationId":"ri.actions.main.action.c61d9ab5-2919-4127-a0a1-ac64c0ce6367","validation":{"result":"VALID"},"parameters":{"id":{"evaluatedConstraints":[],"result":"VALID","required":true},"newName":{"evaluatedConstraints":[],"result":"VALID","required":true}}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| operationId | stringType | False |  |
| validation | objectType | False |  |
| edits | unionType | False |  |

**example:** {"operationId":"ri.actions.main.action.c61d9ab5-2919-4127-a0a1-ac64c0ce6367","validation":{"result":"VALID"},"parameters":{"id":{"evaluatedConstraints":[],"result":"VALID","required":true},"newName":{"evaluatedConstraints":[],"result":"VALID","required":true}}}
