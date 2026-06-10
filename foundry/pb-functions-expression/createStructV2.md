---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/createStructV2/"
title: "Create struct column"
---
# Create struct column

Supported in: Batch, Faster, Streaming. Combines multiple columns into a single structured column. Expression categories: Struct. Declared arguments. Struct elements: List of columns used to create struct. List<Expression<AnyType>> Output type: Struct. Examples. Example 1: Base case. Argument values: Struct elements: [tail_number, id] tail_numberidOutput MT-112. 1. { id: 1, tail_number: MT-112, } XB-123. 2. { id: 2, tail_number: XB-123, } PA-654. 3. { id: 3, tail_number: PA-654, } Example 2: Base case. Argument values: Struct elements: [tail_number, id] tail_numberidOutput null. 1. { id: 1, tail_number: null, } XB-123. null. { id: null, tail_number: XB-123, } null. null. { id: null, tail_number: null, }
