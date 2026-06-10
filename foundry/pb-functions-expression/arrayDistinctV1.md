---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/arrayDistinctV1/"
title: "Array distinct"
---
# Array distinct

Supported in: Batch, Faster, Streaming. Removes duplicates and returns distinct values from the array. Expression categories: Array. Declared arguments. Expression: Input array from which to remove duplicates. Expression<Array<T>> Type variable bounds: T accepts ComparableType. Output type: Array<T> Examples. Example 1: Base case. Argument values: Expression: [ 1, 1, 2, 3 ] Output: [ 1, 2, 3 ] Example 2: Null case. Argument values: Expression: array. arrayOutput null. null.
