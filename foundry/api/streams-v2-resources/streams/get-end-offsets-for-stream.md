---
source_url: "https://www.palantir.com/docs/foundry/api/streams-v2-resources/streams/get-end-offsets-for-stream/"
title: "Get End Offsets For Stream \u2022 API Reference"
---
# Get End Offsets For Stream

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Get the end offsets for all partitions of a stream. The end offset is the offset of the next record that will be written to the partition.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:streams-read`.

**operationId:** v2.getEndOffsetsForStream

**path:** /api/v2/highScale/streams/datasets/{datasetRid}/streams/{streamBranchName}/getEndOffsets

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

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| viewRid | stringType | False | If provided, this endpoint will only read from the stream corresponding to the specified view RID. If not provided, this endpoint will read from the latest stream on the branch.  Providing this value is an advanced configuration, to be used when additional control over the underlying streaming data structures is needed. |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

The end offsets for each partition of a stream.

**name:** GetEndOffsetsResponse

**example:** {"0":100,"1":200}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| PartitionId | stringType | True | The identifier for a partition of a Foundry stream. |

**example:** {"0":100,"1":200}

### Error Responses

| name | description |
| --- | --- |
| GetEndOffsetsForStreamPermissionDenied | Could not getEndOffsets the Stream. |
