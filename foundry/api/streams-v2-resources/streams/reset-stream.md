---
source_url: "https://www.palantir.com/docs/foundry/api/streams-v2-resources/streams/reset-stream/"
title: "Reset Stream \u2022 API Reference"
---
# Reset Stream

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Reset the stream on the given dataset branch, clearing the existing records and allowing new configurations
to be applied.

To change the stream settings without clearing the records, update the stream settings in-platform.

This will create a new stream view (as seen by the change of the `viewRid` on the branch),
which will be the new stream view that will be written to for the branch.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:streams-write`.

**operationId:** v2.resetStream

**path:** /api/v2/streams/datasets/{datasetRid}/streams/{streamBranchName}/reset

### Operation Type

### Scopes

| name |
| --- |
| api:streams-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of a Dataset. |
| streamBranchName | stringType | True | The name of a Branch. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** ResetStreamRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| schema | objectType | False | The Foundry schema to apply to the new stream.   If omitted, the schema of the existing stream on the branch will be used. |
| partitionsCount | integerType | False | The number of partitions for the Foundry stream. Generally, each partition can handle about 5 mb/s of data, so for higher volume streams, more partitions are recommended.  If omitted, the partitions count of the existing stream on the branch will be used. |
| streamType | enumType | False | A conceptual representation of the expected shape of the data for a stream. HIGH_THROUGHPUT and LOW_LATENCY are not compatible with each other. Defaults to LOW_LATENCY.  If omitted, the stream type of the existing stream on the branch will be used. |
| compressed | booleanType | False | Whether or not compression is enabled for the stream.  If omitted, the compression setting of the existing stream on the branch will be used. |

**example:** {"schema":{"fields":[{"name":"timestamp","schema":{"nullable":false,"dataType":{"type":"timestamp"}}},{"name":"value","schema":{"nullable":false,"dataType":{"type":"string"}}}],"keyFieldNames":["timestamp"]},"partitionsCount":1,"streamType":"LOW_LATENCY","compressed":false}

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
| InvalidSchema | The schema failed validations |
| InvalidFieldSchema | The field schema failed validations |
| InvalidStreamNoSchema | The requested stream exists but is invalid, as it does not have a schema. |
| InvalidStreamType | The stream type is invalid. |
| ResetStreamPermissionDenied | Could not reset the Stream. |
| StreamNotFound | The given Stream could not be found. |
