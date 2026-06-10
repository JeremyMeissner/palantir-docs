---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/arrayFlattenV2/"
parquet_url: "/foundry/pb-functions-expression/arrayFlattenV2/"
title: "Array flatten"
fetched_at: "2026-05-12T19:34:36.700Z"
---
Array flatten. Supported in: Batch, Faster, Streaming. Creates a single array from an input nested array by unioning the elements within the first level of nesting. Expression categories: Array. Declared arguments. Expression: Nested array to flatten. Expression<Array<Array<T>>> Type variable bounds: T accepts AnyType. Output type: Array<T> Examples. Example 1: Base case. Argument values: Expression: array. arrayOutput [ [ 1, 2, 3 ], [ 4, 5, 6 ] ] [ 1, 2, 3, 4, 5, 6 ] Example 2: Base case. Argument values: Expression: array. arrayOutput [ [ [ 1 ], [ 2 ] ], [ [ 3 ], [ 4 ] ] ] [ [ 1 ], [ 2 ], [ 3 ], [ 4 ] ] Example 3: Null case. Argument values: Expression: array. arrayOutput null. null. [ null, [ 1, 2 ] ] [ 1, 2 ]
