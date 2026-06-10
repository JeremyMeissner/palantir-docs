---
source_url: "https://www.palantir.com/docs/foundry/api/streams-v2-resources/streams/get-records-from-stream/"
title: "Get Records From Stream \u2022 API Reference"
---
# Get Records From Stream

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Get a batch of records from a stream for a given partition. Offsets are ordered from [0, inf) but may be sparse (e.g.: 0, 2, 3, 5).
Binary field values are returned as base64-encoded strings. Decode them to retrieve the original bytes.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:streams-read`.

**operationId:** v2.getRecordsFromStream

**path:** /api/v2/highScale/streams/datasets/{datasetRid}/streams/{streamBranchName}/getRecords

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
| partitionId | stringType | True | The ID of the partition to retrieve records from. |
| startOffset | stringType | False | The inclusive beginning of the range to be retrieved. Leave empty when reading from the beginning of the partition. |
| limit | integerType | True | The total number of records to be retrieved. The response may contain fewer records than requested depending on number of records in the partition and server-defined limits. |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

A list of records from a stream with their offsets.

**name:** GetRecordsResponse

**example:** [{"offset":42,"value":{"timestamp":1731426022784,"value":"Hello, World!"}}]

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| RecordWithOffset | objectType | True | A record retrieved from a stream, including its offset within the partition. |

**example:** [{"offset":42,"value":{"timestamp":1731426022784,"value":"Hello, World!"}}]

### Error Responses

| name | description |
| --- | --- |
| GetRecordsFromStreamPermissionDenied | Could not getRecords the Stream. |
