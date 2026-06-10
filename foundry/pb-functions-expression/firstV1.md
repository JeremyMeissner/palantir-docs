---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/firstV1/"
parquet_url: "/foundry/pb-functions-expression/firstV1/"
title: "First"
fetched_at: "2026-05-12T19:34:36.575Z"
---
First. Supported in: Batch, Faster, Streaming. First item in the group. Note, if used within an aggregate or unordered window, the row selected will be non-deterministic. Expression categories: Aggregate. Declared arguments. Expression: Expression to aggregate. Expression<T> Ignore nulls: If true, null values will be ignored. Literal<Boolean> Type variable bounds: T accepts AnyType. Output type: T. Examples. Example 1: Base case. Argument values: Expression: values. Ignore nulls: false. Given input table: values null. 2. 4. 3. Outputs: null. Example 2: Base case. Argument values: Expression: values. Ignore nulls: true. Given input table: values null. 2. 4. 3. Outputs: 2.
