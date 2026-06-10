---
source_url: "https://www.palantir.com/docs/foundry/api/streams-v2-resources/streams/publish-records-to-stream/"
title: "Publish Records To Stream \u2022 API Reference"
---
# Publish Records To Stream

## Endpoint

Publish a batch of records to the stream. The records will be validated against the stream's schema, and
the batch will be rejected if one or more of the records are invalid.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:streams-write`.

**operationId:** v2.publishRecordsToStream

**path:** /api/v2/highScale/streams/datasets/{datasetRid}/streams/{streamBranchName}/publishRecords

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

### Request

#### Body

**name:** PublishRecordsToStreamRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| records | listType | False | The records to publish to the stream |
| viewRid | stringType | False | If provided, this endpoint will only write to the stream corresponding to the specified view RID. If not provided, this endpoint will write to the latest stream on the branch.  Providing this value is an advanced configuration, to be used when additional control over the underlying streaming data structures is needed. |

**example:** {"records":[{"timestamp":1731426022784,"value":"Hello, World!"}],"viewRid":"ri.foundry-streaming.main.view.ecd4f0f6-8526-4468-9eda-14939449ad79"}

### Error Responses

| name | description |
| --- | --- |
| PublishRecordsToStreamPermissionDenied | Could not publishRecords the Stream. |
