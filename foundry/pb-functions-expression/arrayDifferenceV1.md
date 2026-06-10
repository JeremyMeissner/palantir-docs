---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/arrayDifferenceV1/"
parquet_url: "/foundry/pb-functions-expression/arrayDifferenceV1/"
title: "Array difference"
fetched_at: "2026-05-12T19:34:36.580Z"
---
Array difference. Supported in: Batch, Faster, Streaming. Returns all unique elements in the left array that are not in the right array. Expression categories: Array. Declared arguments. Left array: no description Expression<Array<T>> Right array: no description Expression<Array<T>> Type variable bounds: T accepts AnyType. Output type: Array<T> Examples. Example 1: Base case. Argument values: Left array: [ 1, 2, 3 ] Right array: [ 2, 3, 4 ] Output: [ 1 ] Example 2: Null case. Argument values: Left array: first_array. Right array: second_array. first_arraysecond_arrayOutput [ 1, 2, 3 ] null. [ 1, 2, 3 ] null. [ 1, 2, 3 ] null. null. null. null. Example 3: Edge case. Description: Duplicates in the left array will be removed. Argument values: Left array: [ 1, 1, 2, 3 ] Right array: [ 2, 3, 4 ] Output: [ 1 ]
