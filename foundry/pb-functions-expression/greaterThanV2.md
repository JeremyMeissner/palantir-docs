---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/greaterThanV2/"
parquet_url: "/foundry/pb-functions-expression/greaterThanV2/"
title: "Greater than"
fetched_at: "2026-05-12T19:34:36.590Z"
---
Greater than. Supported in: Batch, Faster, Streaming. Returns true if left is greater than right. Expression categories: Boolean. Declared arguments. Left: Left expression. Expression<ComparableType> Right: Right expression. Expression<ComparableType> Output type: Boolean. Examples. Example 1: Base case. Argument values: Left: a. Right: b. abOutput 1. 0. true. 1. 1. false. 0. 1. false. Example 2: Base case. Argument values: Left: a. Right: b. abOutput 1. 0.5. true. 1. 1.0. false. Example 3: Base case. Argument values: Left: a. Right: b. abOutput b. a. true. abcd. abc. true. aa. b. false. Example 4: Null case. Argument values: Left: left. Right: right. leftrightOutput null. b. null. b. null. null. null. null. null.
