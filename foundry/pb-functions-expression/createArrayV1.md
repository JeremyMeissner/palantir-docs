---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/createArrayV1/"
parquet_url: "/foundry/pb-functions-expression/createArrayV1/"
title: "Create array"
fetched_at: "2026-05-12T19:34:36.604Z"
---
Create array. Supported in: Batch, Faster, Streaming. Creates an array from the columns provided. Expression categories: Array. Declared arguments. Expressions: A list of expressions to create arrays from. List<Expression<T>> Type variable bounds: T accepts AnyType. Output type: Array<T> Examples. Example 1: Base case. Argument values: Expressions: [1, 2, 3] Output: [ 1, 2, 3 ] Example 2: Base case. Argument values: Expressions: [[ 1 ], [ 2 ]] Output: [ [ 1 ], [ 2 ] ] Example 3: Null case. Argument values: Expressions: [1, null, 3] Output: [ 1, null, 3 ]
