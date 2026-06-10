---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/epochMillisToTimestampV1/"
title: "Epoch milliseconds to timestamp"
---
# Epoch milliseconds to timestamp

Supported in: Batch, Faster, Streaming. Converts from epoch milliseconds to timestamp in UTC. Expression categories: Cast, Datetime. Declared arguments. Expression: Expression containing epoch milliseconds to convert. Expression<Double | Long> Output type: Timestamp. Examples. Example 1: Base case. Description: You can convert epoch timestamps in milliseconds to the timestamp type. Argument values: Expression: 1673964111000. Output: 2023-01-17T14:01:51Z. Example 2: Null case. Description: Null columns remain null. Argument values: Expression: input. inputOutput null. null.
