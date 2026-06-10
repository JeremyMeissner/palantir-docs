---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/arraysCartesianProductV1/"
title: "Array cartesian product"
---
# Array cartesian product

Supported in: Batch, Streaming. Compute the cartesian product of arrays. Expression categories: Array. Declared arguments. Expression: Column to convert base. List<Expression<Array<AnyType>>> Output type: Array<Struct> Examples. Example 1: Base case. Argument values: Expression: [first, second] firstsecondOutput [ [ { s1: 1, }, { s1: 2, } ], [ { s1: 3, } ] ] [ [ { s2: 4, }, { s2: 5, } ], [ { s2: 6, } ] ] [ { first: [ { s1: 1, }, { s1: 2, } ], **secon... Example 2: Base case. Argument values: Expression: [first, second] firstsecondOutput [ 1, 2 ] [ 3, 4 ] [ { first: 1, second: 3, }, { first: 1, *second... Example 3: Base case. Argument values: Expression: [first, second, third] firstsecondthirdOutput [ 1, 2 ] [ word, a ] [ { s1: 1, }, { s1: 2, } ] [ { first: 1, second: word, third: { s1: 1, }... Example 4: Null case. Argument values: Expression: [first, second] firstsecondOutput [ 1, null ] [ null, 4 ] [ { first: 1, second: null, }, { first: 1, **se... [ 1, 2 ] null. [ ] [ ] [ ] [ ] null. null. [ ]
