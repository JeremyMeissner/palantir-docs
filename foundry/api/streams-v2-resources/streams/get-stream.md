---
source_url: "https://www.palantir.com/docs/foundry/api/streams-v2-resources/streams/get-stream/"
title: "Get Stream \u2022 API Reference"
---
# Get Stream

## Endpoint

Get a stream by its branch name. If the branch does not exist, there is no stream on that branch, or the
user does not have permission to access the stream, a 404 error will be returned.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:streams-read`.

**operationId:** v2.getStream

**path:** /api/v2/streams/datasets/{datasetRid}/streams/{streamBranchName}

### Operation Type

### Scopes

| name |
| --- |
| api:streams-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of a Dataset. |
| streamBranchName | stringType | True | The name of a Branch. |

### Response

#### Body

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
| InvalidFieldSchema | The field schema failed validations |
| InvalidStreamNoSchema | The requested stream exists but is invalid, as it does not have a schema. |
| InvalidStreamType | The stream type is invalid. |
| StreamNotFound | The given Stream could not be found. |
