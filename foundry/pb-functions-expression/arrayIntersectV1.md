---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/arrayIntersectV1/"
title: "Array intersect"
---
# Array intersect

Supported in: Batch, Faster, Streaming. Removes duplicates and intersects a list of arrays. Expression categories: Array. Declared arguments. Expressions: A list of arrays to intersect. List<Expression<Array<T>>> Type variable bounds: T accepts AnyType. Output type: Array<T> Examples. Example 1: Base case. Argument values: Expressions: [[ 1, 2, 3 ], [ 3, 4 ]] Output: [ 3 ] Example 2: Base case. Argument values: Expressions: [[ 1, 2, 3 ], [ 3, 4 ], [ 2, 3 ]] Output: [ 3 ] Example 3: Base case. Description: Duplicates are removed. Argument values: Expressions: [[ 1, 1 ], [ 1 ]] Output: [ 1 ] Example 4: Null case. Argument values: Expressions: [first_array, second_array] first_arraysecond_arrayOutput [ 1, 2, 3 ] null. [ ] null. null. [ ]
