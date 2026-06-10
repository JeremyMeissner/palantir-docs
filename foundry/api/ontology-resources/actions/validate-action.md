---
source_url: "https://www.palantir.com/docs/foundry/api/ontology-resources/actions/validate-action/"
title: "Validate Action \u2022 API Reference"
---
# Validate Action

## Endpoint

Validates if an action can be run with the given set of parameters.
The response contains the evaluation of parameters and **submission criteria**
that determine if the request is `VALID` or `INVALID`.
For performance reasons, validations will not consider existing objects or other data in Foundry.
For example, the uniqueness of a primary key or the existence of a user ID will not be checked.
Note that [parameter default values](/docs/foundry/action-types/parameters-default-value/) are not currently supported by
this endpoint. Unspecified parameters will be given a default value of `null`.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontologies-read`.

**operationId:** v1.validateAction

**path:** /api/v1/ontologies/{ontologyRid}/actions/{actionType}/validate

### Operation Type

### Scopes

| name |
| --- |
| api:ontologies-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| ontologyRid | stringType | True | The unique Resource Identifier (RID) of the Ontology that contains the action. To look up your Ontology RID, please use the **List ontologies** endpoint or check the **Ontology Manager**. |
| actionType | stringType | True | The API name of the action to validate. To find the API name for your action, use the **List action types** endpoint or check the **Ontology Manager**. |

### Request

#### Body

**name:** ValidateActionRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| parameters | mapType | False |  |

**example:** {"parameters":{"id":"2","firstName":"Chuck","lastName":"Jones","age":17,"date":"2021-05-01","numbers":[1,2,3],"hasObjectSet":true,"objectSet":"ri.object-set.main.object-set.39a9f4bd-f77e-45ce-9772-70f25852f623","reference":"Chuck","percentage":41.3,"differentObjectId":"2"}}

### Response

#### Body

Success response.

**name:** ValidateActionResponse

**example:** {"result":"INVALID","submissionCriteria":[{"configuredFailureMessage":"First name can not match the first name of the referenced object.","result":"INVALID"}],"parameters":{"age":{"result":"INVALID","evaluatedConstraints":[{"type":"range","gte":18}],"required":true},"id":{"result":"VALID","evaluatedConstraints":[],"required":true},"date":{"result":"VALID","evaluatedConstraints":[],"required":true},"lastName":{"result":"VALID","evaluatedConstraints":[{"type":"oneOf","options":[{"displayName":"Doe","value":"Doe"},{"displayName":"Smith","value":"Smith"},{"displayName":"Adams","value":"Adams"},{"displayName":"Jones","value":"Jones"}],"otherValuesAllowed":true}],"required":true},"numbers":{"result":"VALID","evaluatedConstraints":[{"type":"arraySize","lte":4,"gte":2}],"required":true},"differentObjectId":{"result":"VALID","evaluatedConstraints":[{"type":"objectPropertyValue"}],"required":false},"firstName":{"result":"VALID","evaluatedConstraints":[],"required":true},"reference":{"result":"VALID","evaluatedConstraints":[{"type":"objectQueryResult"}],"required":false},"percentage":{"result":"VALID","evaluatedConstraints":[{"type":"range","lt":100,"gte":0}],"required":true},"objectSet":{"result":"VALID","evaluatedConstraints":[],"required":true},"attachment":{"result":"VALID","evaluatedConstraints":[],"required":false},"hasObjectSet":{"result":"VALID","evaluatedConstraints":[],"required":false},"multipleAttachments":{"result":"VALID","evaluatedConstraints":[{"type":"arraySize","gte":0}],"required":false}}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| result | enumType | True | Represents the state of a validation. |
| submissionCriteria | listType | False |  |
| parameters | mapType | False |  |

**example:** {"result":"INVALID","submissionCriteria":[{"configuredFailureMessage":"First name can not match the first name of the referenced object.","result":"INVALID"}],"parameters":{"age":{"result":"INVALID","evaluatedConstraints":[{"type":"range","gte":18}],"required":true},"id":{"result":"VALID","evaluatedConstraints":[],"required":true},"date":{"result":"VALID","evaluatedConstraints":[],"required":true},"lastName":{"result":"VALID","evaluatedConstraints":[{"type":"oneOf","options":[{"displayName":"Doe","value":"Doe"},{"displayName":"Smith","value":"Smith"},{"displayName":"Adams","value":"Adams"},{"displayName":"Jones","value":"Jones"}],"otherValuesAllowed":true}],"required":true},"numbers":{"result":"VALID","evaluatedConstraints":[{"type":"arraySize","lte":4,"gte":2}],"required":true},"differentObjectId":{"result":"VALID","evaluatedConstraints":[{"type":"objectPropertyValue"}],"required":false},"firstName":{"result":"VALID","evaluatedConstraints":[],"required":true},"reference":{"result":"VALID","evaluatedConstraints":[{"type":"objectQueryResult"}],"required":false},"percentage":{"result":"VALID","evaluatedConstraints":[{"type":"range","lt":100,"gte":0}],"required":true},"objectSet":{"result":"VALID","evaluatedConstraints":[],"required":true},"attachment":{"result":"VALID","evaluatedConstraints":[],"required":false},"hasObjectSet":{"result":"VALID","evaluatedConstraints":[],"required":false},"multipleAttachments":{"result":"VALID","evaluatedConstraints":[{"type":"arraySize","gte":0}],"required":false}}}
