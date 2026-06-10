---
source_url: "https://www.palantir.com/docs/foundry/api/v2/streams-v2-resources/streams/publish-binary-record-to-stream/"
parquet_url: "/foundry/api/v2/streams-v2-resources/streams/publish-binary-record-to-stream/"
title: "Publish Binary Record To Stream"
fetched_at: "2026-05-12T19:34:37.595Z"
---
Publish Binary Record To Stream. Publish a single binary record to the stream. The stream's schema must be a single binary field. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:streams-write. Path parameters. The Resource Identifier (RID) of a Dataset. The name of a Branch. Query parameters. If provided, this endpoint will only write to the stream corresponding to the specified view RID. If not provided, this endpoint will write to the latest stream on the branch. Providing this value is an advanced configuration, to be used when additional control over the underlying streaming data structures is needed. Request body. The binary record to publish to the stream. Examples. Error responses.
