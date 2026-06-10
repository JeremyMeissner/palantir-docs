---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/leftStringV1/"
parquet_url: "/foundry/pb-functions-expression/leftStringV1/"
title: "Left of string"
fetched_at: "2026-05-12T19:34:36.649Z"
---
Left of string. Supported in: Batch, Faster, Streaming. Extract left hand side of a string based on index. Expression categories: String. Declared arguments. Expression: String input expression. Expression<String> Length: The number of characters to take from the left of the string. Expression<Integer> Output type: String. Examples. Example 1: Base case. Argument values: Expression: Hello world! Length: 5. Output: Hello. Example 2: Null case. Argument values: Expression: string. Length: length. stringlengthOutput Hello world! -10. empty string. Example 3: Null case. Argument values: Expression: string. Length: length. stringlengthOutput null. 1. null. Hello world! null. null. null. null. null. Example 4: Edge case. Description: Length greater than the string length will return the full string. Argument values: Expression: Hello world! Length: 15. Output: Hello world!
