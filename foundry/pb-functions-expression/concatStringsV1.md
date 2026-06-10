---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/concatStringsV1/"
parquet_url: "/foundry/pb-functions-expression/concatStringsV1/"
title: "Concatenate strings"
fetched_at: "2026-05-12T19:34:36.639Z"
---
Concatenate strings. Supported in: Batch, Faster, Streaming. Concatenates a list of strings with the specified separator. Expression categories: String. Declared arguments. Expressions: List of strings to be concatenated. List<Expression<String>> optional Null output if any input is null: If any of the input values are null, then the output should be null. If false, null values in the input are ignored. Literal<Boolean> optional Separator: Separator to be added between the strings. Literal<String> Output type: String. Examples. Example 1: Base case. Argument values: Expressions: [hello, world] Null output if any input is null: null. Separator: _. Output: hello_world. Example 2: Null case. Argument values: Expressions: [hello, null, world, !] Null output if any input is null: null. Separator: -- Output: hello--world--! Example 3: Null case. Argument values: Expressions: [hello, null, world, !] Null output if any input is null: true. Separator: -- Output: null.
