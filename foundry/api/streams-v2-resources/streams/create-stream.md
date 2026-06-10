---
source_url: "https://www.palantir.com/docs/foundry/api/streams-v2-resources/streams/create-stream/"
title: "Create Stream \u2022 API Reference"
---
# Create Stream

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Creates a new branch on the backing streaming dataset, and creates a new stream on that branch.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:streams-write`.

**operationId:** v2.createStream

**path:** /api/v2/streams/datasets/{datasetRid}/streams

### Operation Type

### Scopes

| name |
| --- |
| api:streams-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of a Dataset. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** CreateStreamRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| schema | objectType | True | The Foundry schema for this stream. |
| partitionsCount | integerType | False | The number of partitions for the Foundry stream. Defaults to 1.  Generally, each partition can handle about 5 mb/s of data, so for higher volume streams, more partitions are recommended. |
| streamType | enumType | False | A conceptual representation of the expected shape of the data for a stream. HIGH_THROUGHPUT and LOW_LATENCY are not compatible with each other. Defaults to LOW_LATENCY. |
| branchName | stringType | True | The name of a Branch. |
| compressed | booleanType | False | Whether or not compression is enabled for the stream. Defaults to false. |

**example:** {"partitionsCount":1,"streamType":"LOW_LATENCY","branchName":"master","compressed":false}

### Response

#### Body

The created Stream

**name:** Stream

**example:** {"schema":{"fields":[{"name":"timestamp","schema":{"nullable":false,"dataType":{"type":"timestamp"}}},{"name":"value","schema":{"nullable":false,"dataType":{"type":"string"}}}],"keyFieldNames":["timestamp"]},"partitionsCount":1,"streamType":"LOW_LATENCY","branchName":"master","viewRid":"ri.foundry-streaming.main.view.ecd4f0f6-8526-4468-9eda-14939449ad79","compressed":false}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| branchName | stringType | True | The name of a Branch. |
| schema | objectType | True | The Foundry schema for this stream. |
| viewRid | stringType | True | The view that this stream corresponds to. |
| partitionsCount | integerType | True | The number of partitions for the Foundry stream. Defaults to 1.  Generally, each partition can handle about 5 mb/s of data, so for higher volume streams, more partitions are recommended. |
| streamType | enumType | True | A conceptual representation of the expected shape of the data for a stream. HIGH_THROUGHPUT and LOW_LATENCY are not compatible with each other. Defaults to LOW_LATENCY. |
| compressed | booleanType | True | Whether or not compression is enabled for the stream. Defaults to false. |

**example:** {"schema":{"fields":[{"name":"timestamp","schema":{"nullable":false,"dataType":{"type":"timestamp"}}},{"name":"value","schema":{"nullable":false,"dataType":{"type":"string"}}}],"keyFieldNames":["timestamp"]},"partitionsCount":1,"streamType":"LOW_LATENCY","branchName":"master","viewRid":"ri.foundry-streaming.main.view.ecd4f0f6-8526-4468-9eda-14939449ad79","compressed":false}

### Error Responses

| name | description |
| --- | --- |
| BranchAlreadyExists | The branch cannot be created because a branch with that name already exists. |
| InvalidSchema | The schema failed validations |
| InvalidFieldSchema | The field schema failed validations |
| InvalidStreamType | The stream type is invalid. |
| CreateStreamPermissionDenied | Could not create the Stream. |
