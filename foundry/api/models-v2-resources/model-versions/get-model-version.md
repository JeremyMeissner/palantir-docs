---
source_url: "https://www.palantir.com/docs/foundry/api/models-v2-resources/model-versions/get-model-version/"
title: "Get Model Version \u2022 API Reference"
---
# Get Model Version

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Retrieves a Model Version by its Resource Identifier (RID).

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:models-read`.

**operationId:** v2.getModelVersion

**path:** /api/v2/models/{modelRid}/versions/{modelVersionRid}

### Operation Type

### Scopes

| name |
| --- |
| api:models-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| modelRid | stringType | True | The Resource Identifier (RID) of a Model. |
| modelVersionRid | stringType | True | The Resource Identifier (RID) of a Model Version. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** ModelVersion

**example:** {"backingRepositories":["ri.stemma.main.repository.a1b2c3d4-e5f6-7890-abcd-ef1234567890"],"condaRequirements":["numpy==1.24.0","pandas==2.0.0"],"linkedExperiment":"ri.models.main.experiment.abc123","modelApi":{"inputs":[{"name":"input_df","required":true,"type":"tabular","columns":[{"name":"feature_1","required":true,"dataType":{"type":"double"}},{"name":"feature_2","required":true,"dataType":{"type":"integer"}}],"format":"PANDAS"}],"outputs":[{"name":"output_df","required":true,"type":"tabular","columns":[{"name":"prediction","required":true,"dataType":{"type":"double"}}],"format":"SPARK"}]},"createdTime":"2003-05-06T12:34:56.789Z","rid":"ri.models.main.model-version.adf94926-c3ac-41ea-beb2-4946699d08ee"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The Resource Identifier (RID) of a Model Version. |
| modelApi | objectType | True | The Model API is a specification that describes the inputs and outputs of a machine learning model. It is used to define the interface for the model, including the types of data that can be passed to it and the types of data that it will return. |
| condaRequirements | listType | False |  |
| backingRepositories | listType | False |  |
| createdTime | stringType | True | The time at which the resource was created. |
| source | unionType | False | The source from which this model version was created. |
| linkedExperiment | stringType | False | The Experiment linked to this Model Version, if one exists. |

**example:** {"backingRepositories":["ri.stemma.main.repository.a1b2c3d4-e5f6-7890-abcd-ef1234567890"],"condaRequirements":["numpy==1.24.0","pandas==2.0.0"],"linkedExperiment":"ri.models.main.experiment.abc123","modelApi":{"inputs":[{"name":"input_df","required":true,"type":"tabular","columns":[{"name":"feature_1","required":true,"dataType":{"type":"double"}},{"name":"feature_2","required":true,"dataType":{"type":"integer"}}],"format":"PANDAS"}],"outputs":[{"name":"output_df","required":true,"type":"tabular","columns":[{"name":"prediction","required":true,"dataType":{"type":"double"}}],"format":"SPARK"}]},"createdTime":"2003-05-06T12:34:56.789Z","rid":"ri.models.main.model-version.adf94926-c3ac-41ea-beb2-4946699d08ee"}

### Error Responses

| name | description |
| --- | --- |
| UnsupportedModelSource | The Model Version has a source type that is not supported by the API. This can occur when the model was created through a legacy or internal workflow that is not exposed through the public API. |
| ModelVersionNotFound | The given ModelVersion could not be found. |
