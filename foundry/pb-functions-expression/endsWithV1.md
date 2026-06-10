---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/endsWithV1/"
parquet_url: "/foundry/pb-functions-expression/endsWithV1/"
title: "Ends with"
fetched_at: "2026-05-12T19:34:36.687Z"
---
Ends with. Supported in: Batch, Faster, Streaming. Expression categories: Boolean, String. Declared arguments. Expression: Expression to compare. Expression<String> Ignore case: Boolean to decide if comparison should be case-sensitive or not. Literal<Boolean> Value: Value to compare against. Expression<String> Output type: Boolean. Examples. Example 1: Base case. Argument values: Expression: Hello World. Ignore case: false. Value: world. Output: false. Example 2: Base case. Argument values: Expression: Hello World. Ignore case: false. Value: World. Output: true. Example 3: Base case. Argument values: Expression: Hello World. Ignore case: true. Value: world. Output: true. Example 4: Null case. Argument values: Expression: null. Ignore case: false. Value: null. Output: false. Example 5: Null case. Argument values: Expression: null. Ignore case: false. Value: World. Output: false. Example 6: Null case. Argument values: Expression: Hello World. Ignore case: false. Value: null. Output: false.
