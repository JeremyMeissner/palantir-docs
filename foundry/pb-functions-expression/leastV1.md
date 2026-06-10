---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/leastV1/"
parquet_url: "/foundry/pb-functions-expression/leastV1/"
title: "Least"
fetched_at: "2026-05-12T19:34:36.677Z"
---
Least. Supported in: Batch, Faster, Streaming. Computes the least value amongst all input columns, skipping null values. Expression categories: Boolean, Numeric. Declared arguments. Expressions: no description List<Expression<T>> Type variable bounds: T accepts ComparableType. Output type: T. Examples. Example 1: Base case. Argument values: Expressions: [a, b, c] abcOutput 1. 2. 3. 1. 1. 3. 2. 1. 3. 2. 1. 1. Example 2: Null case. Description: Returns null if values of all inputs are null. Argument values: Expressions: [a, b] abOutput null. null. null. Example 3: Null case. Description: Any null values are ignored for comparison purposes. Argument values: Expressions: [a, b] abOutput null. -2147483648. -2147483648. null. 0. 0. null. 2147483647. 2147483647.
