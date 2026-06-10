---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/leftPadV1/"
title: "Left pad string"
---
# Left pad string

Supported in: Batch, Faster, Streaming. Left-pad the string column to width of length with pad. Expression categories: String. Declared arguments. Expression: no description Expression<String> Length: no description Expression<Integer> Pad: no description Expression<String> Output type: String. Examples. Example 1: Base case. Argument values: Expression: Hello world! Length: 15. Pad: *. Output: ***Hello world! Example 2: Null case. Argument values: Expression: String. Length: Length. Pad: Pad. StringLengthPadOutput null. 15. *. null. Hello world! null. *. empty string. Hello, world! 15. null. Hello, world! null. null. null. null. Example 3: Edge case. Description: Length less than the string, it will truncate the string. Argument values: Expression: Hello world! Length: 5. Pad: *. Output: Hello. Example 4: Edge case. Description: Length of 0 will remove the string. Argument values: Expression: Hello world! Length: 0. Pad: *. Output: empty string.
