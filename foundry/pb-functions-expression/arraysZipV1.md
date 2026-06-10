---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/arraysZipV1/"
title: "Arrays zip"
---
# Arrays zip

Supported in: Batch, Faster, Streaming. Zips a list of given arrays into a merged array of structs in which the n-th struct contains all n-th values of input arrays. Expression categories: Array. Declared arguments. Expressions: A list of arrays to zip. List<Expression<Array<AnyType>>> Output type: Array<Struct> Examples. Example 1: Base case. Argument values: Expressions: [first_array, second_array] first_arraysecond_arrayOutput [ 1, 2, 3 ] [ 4, 5, 6 ] [ { first_array: 1, second_array: 4, }, { first_array: 2,<... Example 2: Null case. Argument values: Expressions: [first_array, second_array] first_arraysecond_arrayOutput [ 1, 2, 3 ] null. [ { first_array: 1, second_array: null, }, { first_array... null. null. [ ] [ ] [ ] [ ] Example 3: Edge case. Description: Longest length array is used. Argument values: Expressions: [first_array, second_array] first_arraysecond_arrayOutput [ 1, 2, 3 ] [ 4, 5 ] [ { first_array: 1, second_array: 4, }, { first_array: 2,<...
