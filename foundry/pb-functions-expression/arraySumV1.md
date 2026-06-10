---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/arraySumV1/"
title: "Sum of array elements"
---
# Sum of array elements

Supported in: Batch, Faster, Streaming. Sums the elements contained within the array. Expression categories: Array. Declared arguments. Expression: An array of numeric types to be summed. Expression<Array<T>> optional Treat null as zero: If true, nulls inside the array are treated as zero, and arrays containing null can be summed. If false, the presence of a null makes the entire array null. Literal<Boolean> Type variable bounds: T accepts DefiniteNumeric. Output type: T. Examples. Example 1: Base case. Argument values: Expression: [ 1, 2, 3 ] Treat null as zero: true. Output: 6. Example 2: Null case. Argument values: Expression: [ 1, 2, 3, null ] Treat null as zero: false. Output: null. Example 3: Null case. Argument values: Expression: [ 1, 2, 3, null ] Treat null as zero: true. Output: 6. Example 4: Null case. Argument values: Expression: array. Treat null as zero: true. arrayOutput null. null.
