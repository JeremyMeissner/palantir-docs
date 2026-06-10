---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/skipBytesV1/"
parquet_url: "/foundry/pb-functions-expression/skipBytesV1/"
title: "Skip bytes"
fetched_at: "2026-05-12T19:34:36.654Z"
---
Skip bytes. Supported in: Batch, Faster, Streaming. Skip a given number of bytes in a binary column. Expression categories: Binary. Declared arguments. Bytes: no description Expression<Binary> Number of bytes to skip: no description Expression<Integer> Output type: Binary. Examples. Example 1: Base case. Argument values: Bytes: aGk= Number of bytes to skip: 1. Output: aQ== Example 2: Null case. Argument values: Bytes: null. Number of bytes to skip: 1. Output: null. Example 3: Null case. Argument values: Bytes: aGk= Number of bytes to skip: null. Output: null. Example 4: Edge case. Argument values: Bytes: aGk= Number of bytes to skip: 100. Output: null.
