---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/arrayConcatV1/"
parquet_url: "/foundry/pb-functions-expression/arrayConcatV1/"
title: "Array concat"
fetched_at: "2026-05-12T19:34:36.571Z"
---
Array concat. Supported in: Batch, Faster, Streaming. Concatenates the provided arrays into a single array, without de-duplication. Expression categories: Array. Declared arguments. Expressions: A list of arrays to concatenate. List<Expression<Array<T>>> Type variable bounds: T accepts AnyType. Output type: Array<T> Examples. Example 1: Base case. Argument values: Expressions: [[ 1, 2, 3 ], [ 4, 5 ]] Output: [ 1, 2, 3, 4, 5 ] Example 2: Base case. Argument values: Expressions: [[ 1, 2, 3 ], [ 3, 4 ], [ 4, 5 ]] Output: [ 1, 2, 3, 3, 4, 4, 5 ] Example 3: Base case. Argument values: Expressions: [[ 1, 2, 3 ], [ 3, 4 ]] Output: [ 1, 2, 3, 3, 4 ] Example 4: Null case. Argument values: Expressions: [first_array, second_array] first_arraysecond_arrayOutput [ 1, 2 ] [ 3, 4 ] [ 1, 2, 3, 4 ] [ 1, 2, 3 ] null. [ 1, 2, 3 ] null. null. [ ]
