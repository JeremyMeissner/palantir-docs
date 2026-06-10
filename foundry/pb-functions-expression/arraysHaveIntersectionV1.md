---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/arraysHaveIntersectionV1/"
title: "Arrays have intersection"
---
# Arrays have intersection

Supported in: Batch, Faster, Streaming. Checks if given arrays have at least one shared element. Expression categories: Array, Boolean. Declared arguments. Expressions: List of arrays to check. List<Expression<Array<T>>> Type variable bounds: T accepts AnyType. Output type: Boolean. Examples. Example 1: Base case. Argument values: Expressions: [[ 1, 2, 3 ], [ 3, 4 ]] Output: true. Example 2: Base case. Argument values: Expressions: [[ 1, 2 ], [ 3, 4 ]] Output: false. Example 3: Base case. Argument values: Expressions: [[ 1, 2, 3 ], [ 3, 4 ], [ 2, 3 ]] Output: true. Example 4: Null case. Argument values: Expressions: [first_array, second_array] first_arraysecond_arrayOutput [ 1, 2, 3 ] null. false. null. null. false.
