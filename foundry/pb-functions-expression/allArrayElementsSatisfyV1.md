---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/allArrayElementsSatisfyV1/"
title: "All array elements satisfy"
---
# All array elements satisfy

Supported in: Batch, Streaming. Return true if the expression is true for all elements in the array. Expression categories: Array. Declared arguments. Array: Array expression. Expression<Array<AnyType>> Boolean condition: The expression to apply once per element of the array. Expression<Boolean> Output type: Boolean. Examples. Example 1: Base case. Argument values: Array: miles. Boolean condition: lessThan( left: element, right: base_line, ). milesbase_lineOutput [ 12300, 10150 ] 20000. true. Example 2: Base case. Argument values: Array: miles. Boolean condition: isNull( expression: element, ). milesOutput [ 12300, null ] false. [ null, null ] true. Example 3: Base case. Argument values: Array: boolean_array. Boolean condition: element. boolean_arrayOutput [ true, false ] false. [ false, false ] false. [ true, true ] true. Example 4: Null case. Description: Null arrays will return null outputs. Argument values: Array: miles. Boolean condition: isNull( expression: element, ). milesOutput null. null.
