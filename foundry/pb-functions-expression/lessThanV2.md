---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/lessThanV2/"
parquet_url: "/foundry/pb-functions-expression/lessThanV2/"
title: "Less than"
fetched_at: "2026-05-12T19:34:36.599Z"
---
Less than. Supported in: Batch, Faster, Streaming. Returns true if left is less than right. Expression categories: Boolean. Declared arguments. Left: Left expression. Expression<ComparableType> Right: Right expression. Expression<ComparableType> Output type: Boolean. Examples. Example 1: Base case. Argument values: Left: left. Right: right. leftrightOutput 1.0. 10. true. 10.0. 1. false. Example 2: Base case. Argument values: Left: left. Right: right. leftrightOutput a. b. true. b. a. false. Example 3: Null case. Argument values: Left: left. Right: right. leftrightOutput [ { field1: a, field2: aa, } ] [ { field1: b, field2: bb, } ] true. Example 4: Null case. Argument values: Left: left. Right: right. leftrightOutput null. b. null. b. null. null. null. null. null.
