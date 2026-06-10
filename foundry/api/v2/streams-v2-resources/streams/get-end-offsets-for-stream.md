---
source_url: "https://www.palantir.com/docs/foundry/api/v2/streams-v2-resources/streams/get-end-offsets-for-stream/"
parquet_url: "/foundry/api/v2/streams-v2-resources/streams/get-end-offsets-for-stream/"
title: "Get End Offsets For Stream"
fetched_at: "2026-05-12T19:34:37.597Z"
---
Get End Offsets For Stream. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Get the end offsets for all partitions of a stream. The end offset is the offset of the next record that will be written to the partition. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:streams-read. Path parameters. The Resource Identifier (RID) of a Dataset. The name of a Branch. Query parameters. If provided, this endpoint will only read from the stream corresponding to the specified view RID. If not provided, this endpoint will read from the latest stream on the branch. Providing this value is an advanced configuration, to be used when additional control over the underlying streaming data structures is needed. Enables the use of preview functionality. Response body. The end offsets for each partition of a stream. The identifier for a partition of a Foundry stream. Examples. Error responses.
