---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/rightStringV1/"
parquet_url: "/foundry/pb-functions-expression/rightStringV1/"
title: "Right of string"
fetched_at: "2026-05-12T19:34:36.701Z"
---
Right of string. Supported in: Batch, Faster, Streaming. Extract right hand side of a string based on index. Expression categories: String. Declared arguments. Expression: no description Expression<String> Length: The number of characters to take from the right of the string. Expression<Integer> Output type: String. Examples. Example 1: Base case. Argument values: Expression: Hello world! Length: 6. Output: world! Example 2: Null case. Argument values: Expression: String. Length: Length. StringLengthOutput null. 1. null. Hello world! null. null. null. null. null. Example 3: Edge case. Description: Length greater than the string length will return the full string. Argument values: Expression: Hello world! Length: 15. Output: Hello world!
