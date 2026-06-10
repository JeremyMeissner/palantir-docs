---
source_url: "https://www.palantir.com/docs/foundry/api/models-v2-resources/model-versions/list-model-versions/"
title: "List Model Versions \u2022 API Reference"
---
# List Model Versions

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Lists all Model Versions for a given Model.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:models-read`.

**operationId:** v2.listModelVersions

**path:** /api/v2/models/{modelRid}/versions

### Operation Type

### Scopes

| name |
| --- |
| api:models-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| modelRid | stringType | True | The Resource Identifier (RID) of a Model. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branch | stringType | False | The branch to list versions from. Defaults to master on most enrollments. |
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** ListModelVersionsResponse

**example:** {"data":[{"backingRepositories":["ri.stemma.main.repository.a1b2c3d4-e5f6-7890-abcd-ef1234567890"],"condaRequirements":["numpy==1.24.0","pandas==2.0.0"],"linkedExperiment":"ri.models.main.experiment.abc123","modelApi":{"inputs":[{"name":"input_df","required":true,"type":"tabular","columns":[{"name":"feature_1","required":true,"dataType":{"type":"double"}},{"name":"feature_2","required":true,"dataType":{"type":"integer"}}],"format":"PANDAS"}],"outputs":[{"name":"output_df","required":true,"type":"tabular","columns":[{"name":"prediction","required":true,"dataType":{"type":"double"}}],"format":"SPARK"}]},"createdTime":"2003-05-06T12:34:56.789Z","rid":"ri.models.main.model-version.adf94926-c3ac-41ea-beb2-4946699d08ee"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"backingRepositories":["ri.stemma.main.repository.a1b2c3d4-e5f6-7890-abcd-ef1234567890"],"condaRequirements":["numpy==1.24.0","pandas==2.0.0"],"linkedExperiment":"ri.models.main.experiment.abc123","modelApi":{"inputs":[{"name":"input_df","required":true,"type":"tabular","columns":[{"name":"feature_1","required":true,"dataType":{"type":"double"}},{"name":"feature_2","required":true,"dataType":{"type":"integer"}}],"format":"PANDAS"}],"outputs":[{"name":"output_df","required":true,"type":"tabular","columns":[{"name":"prediction","required":true,"dataType":{"type":"double"}}],"format":"SPARK"}]},"createdTime":"2003-05-06T12:34:56.789Z","rid":"ri.models.main.model-version.adf94926-c3ac-41ea-beb2-4946699d08ee"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| UnsupportedModelSource | The Model Version has a source type that is not supported by the API. This can occur when the model was created through a legacy or internal workflow that is not exposed through the public API. |
| ModelNotFound | The given Model could not be found. |
