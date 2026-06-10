---
source_url: "https://www.palantir.com/docs/foundry/api/streams-v2-resources/streams/publish-binary-record-to-stream/"
title: "Publish Binary Record To Stream \u2022 API Reference"
---
# Publish Binary Record To Stream

## Endpoint

Publish a single binary record to the stream. The stream's schema must be a single binary field.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:streams-write`.

**operationId:** v2.publishBinaryRecordToStream

**path:** /api/v2/highScale/streams/datasets/{datasetRid}/streams/{streamBranchName}/publishBinaryRecord

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
| viewRid | stringType | False | If provided, this endpoint will only write to the stream corresponding to the specified view RID. If not provided, this endpoint will write to the latest stream on the branch.  Providing this value is an advanced configuration, to be used when additional control over the underlying streaming data structures is needed. |

### Request

#### Body

The binary record to publish to the stream

**name:** body

##### Format

### Error Responses

| name | description |
| --- | --- |
| PublishBinaryRecordToStreamPermissionDenied | Could not publishBinaryRecord the Stream. |
