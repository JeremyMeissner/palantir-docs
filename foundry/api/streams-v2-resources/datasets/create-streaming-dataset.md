---
source_url: "https://www.palantir.com/docs/foundry/api/streams-v2-resources/datasets/create-streaming-dataset/"
title: "Create Streaming Dataset \u2022 API Reference"
---
# Create Streaming Dataset

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Creates a streaming dataset with a stream on the specified branch, or if no branch is specified, on the
default branch ('master' for most enrollments). For more information on streaming datasets, refer to the
[streams](/docs/foundry/data-integration/streams/) user documentation.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:streams-write`.

**operationId:** v2.createStreamingDataset

**path:** /api/v2/streams/datasets/create

### Operation Type

### Scopes

| name |
| --- |
| api:streams-write |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** CreateStreamingDatasetRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| name | stringType | True |  |
| parentFolderRid | stringType | True | The unique resource identifier (RID) of a Folder. |
| schema | objectType | True | The Foundry schema to apply to the new stream. |
| branchName | stringType | False | The branch to create the initial stream on. If not specified, the default branch will be used ('master' for most enrollments). |
| partitionsCount | integerType | False | The number of partitions for the Foundry stream.  Generally, each partition can handle about 5 mb/s of data, so for higher volume streams, more partitions are recommended.  If not specified, 1 partition is used.  This value cannot be changed later. |
| streamType | enumType | False | A conceptual representation of the expected shape of the data for a stream. HIGH_THROUGHPUT and LOW_LATENCY are not compatible with each other. Defaults to LOW_LATENCY. |
| compressed | booleanType | False | Whether or not compression is enabled for the stream. Defaults to false. |

**example:** {"parentFolderRid":"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791","schema":{"fields":[{"name":"timestamp","schema":{"nullable":false,"dataType":{"type":"timestamp"}}},{"name":"value","schema":{"nullable":false,"dataType":{"type":"string"}}}],"keyFieldNames":["timestamp"]},"partitionsCount":1,"streamType":"LOW_LATENCY","name":"My Dataset","branchName":"master","compressed":false}

### Response

#### Body

**name:** Dataset

**example:** {"parentFolderRid":"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791","name":"My Dataset","rid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The Resource Identifier (RID) of a Dataset. |
| name | stringType | True |  |
| parentFolderRid | stringType | True | The unique resource identifier (RID) of a Folder. |

**example:** {"parentFolderRid":"ri.compass.main.folder.c410f510-2937-420e-8ea3-8c9bcb3c1791","name":"My Dataset","rid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da"}

### Error Responses

| name | description |
| --- | --- |
| ResourceNameAlreadyExists | The provided resource name is already in use by another resource in the same folder. |
| InvalidSchema | The schema failed validations |
| InvalidFieldSchema | The field schema failed validations |
| CannotCreateStreamingDatasetInUserFolder | Cannot create a streaming dataset in a user folder. |
| InvalidStreamType | The stream type is invalid. |
| CreateStreamingDatasetPermissionDenied | Could not create the Dataset. |
