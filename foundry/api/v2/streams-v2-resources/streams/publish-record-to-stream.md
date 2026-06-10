---
source_url: "https://www.palantir.com/docs/foundry/api/v2/streams-v2-resources/streams/publish-record-to-stream/"
title: "Publish Record To Stream"
---
# Publish Record To Stream

Publish a single record to the stream. The record will be validated against the stream's schema, and rejected if it is invalid. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:streams-write. Path parameters. The Resource Identifier (RID) of a Dataset. The name of a Branch. Request body. The record to publish to the stream. If provided, this endpoint will only write to the stream corresponding to the specified view RID. If not provided, this endpoint will write the latest stream on the branch. Providing this value is an advanced configuration, to be used when additional control over the underlying streaming data structures is needed. Examples. Error responses.
