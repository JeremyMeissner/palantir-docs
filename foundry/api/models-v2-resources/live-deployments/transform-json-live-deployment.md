---
source_url: "https://www.palantir.com/docs/foundry/api/models-v2-resources/live-deployments/transform-json-live-deployment/"
title: "Transform Json Live Deployment \u2022 API Reference"
---
# Transform Json Live Deployment

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Performs inference on the live deployment.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:models-execute`.

**operationId:** v2.transformJsonLiveDeployment

**path:** /api/v2/models/liveDeployments/{liveDeploymentRid}/transformJson

### Operation Type

### Scopes

| name |
| --- |
| api:models-execute |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| liveDeploymentRid | stringType | True | The Resource Identifier (RID) of a Live Deployment. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** TransformJsonLiveDeploymentRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| input | mapType | False | The input data for the model inference. The structure should match the model's transform API specification, where each key is an input name and the value is the corresponding input data. |

**example:** {"input":{"input_df":[{"feature_1":1.0,"feature_2":2}]}}

### Response

#### Body

The response from transforming input data using a live deployment.

**name:** TransformLiveDeploymentResponse

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| output | mapType | False | The output data from the model inference. The structure depends on the model's defined API specification, where each key is an output name and the value is the corresponding output data. |

### Error Responses

| name | description |
| --- | --- |
| LiveDeploymentNotFound | The specified live deployment was not found. |
| InferenceTimeout | The live deployment took longer than 5 minutes to respond to the inference request. This typically indicates the model execution is taking too long or the deployment is under heavy load. |
| InferenceInvalidInput | The inference request contains invalid input data that does not match the model's API specification. Check the error type for specific validation failure details. |
| InferenceFailure | The inference request failed due to a model execution error or unexpected internal issue. This typically indicates a problem with the model itself rather than the input data. |
| TransformJsonLiveDeploymentPermissionDenied | Could not transformJson the LiveDeployment. |
