---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/equalsV1/"
parquet_url: "/foundry/pb-functions-expression/equalsV1/"
title: "Equals"
fetched_at: "2026-05-12T19:34:36.685Z"
---
Equals. Supported in: Batch, Faster, Streaming. Returns true if left and right are equal. Expression categories: Boolean. Declared arguments. Left: Left expression. Expression<ComparableType> Right: Right expression. Expression<ComparableType> Output type: Boolean. Examples. Example 1: Base case. Argument values: Left: a. Right: b. abOutput 1. 1. true. 1. 0. false. Example 2: Base case. Argument values: Left: a. Right: b. abOutput 1.0. 1. true. 1.0. 0. false. Example 3: Base case. Argument values: Left: departure. Right: destination. departuredestinationOutput Heathrow. Heathrow. true. Heathrow. Gatwick. false. Example 4: Null case. Argument values: Left: departure. Right: destination. departuredestinationOutput null. null. true. null. Heathrow. false.
