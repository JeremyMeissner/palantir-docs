---
source_url: "https://www.palantir.com/docs/foundry/api/v2/models-v2-resources/live-deployments/transform-json-live-deployment/"
title: "Transform Json Live Deployment"
---
# Transform Json Live Deployment

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Performs inference on the live deployment. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:models-execute. Path parameters. The Resource Identifier (RID) of a Live Deployment. Query parameters. Enables the use of preview functionality. Request body. The input data for the model inference. The structure should match the model's transform API specification, where each key is an input name and the value is the corresponding input data. Response body. The response from transforming input data using a live deployment. The output data from the model inference. The structure depends on the model's defined API specification, where each key is an output name and the value is the corresponding output data. Examples. Error responses.
