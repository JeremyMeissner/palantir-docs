---
source_url: "https://www.palantir.com/docs/foundry/api/v2/streams-v2-resources/streams/get-stream/"
title: "Get Stream"
---
# Get Stream

Get a stream by its branch name. If the branch does not exist, there is no stream on that branch, or the user does not have permission to access the stream, a 404 error will be returned. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:streams-read. Path parameters. The Resource Identifier (RID) of a Dataset. The name of a Branch. Response body. The name of a Branch. The Foundry schema for this stream. The view that this stream corresponds to. The number of partitions for the Foundry stream. Defaults to 1. Generally, each partition can handle about 5 mb/s of data, so for higher volume streams, more partitions are recommended. A conceptual representation of the expected shape of the data for a stream. HIGH_THROUGHPUT and LOW_LATENCY are not compatible with each other. Defaults to LOW_LATENCY. Enum values: LOW_LATENCY, HIGH_THROUGHPUT. Whether or not compression is enabled for the stream. Defaults to false. Examples. Error responses.
