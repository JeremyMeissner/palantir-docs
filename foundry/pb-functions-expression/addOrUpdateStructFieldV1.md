---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/addOrUpdateStructFieldV1/"
title: "Add or update struct field"
---
# Add or update struct field

Supported in: Batch, Faster, Streaming. Updates a field of a struct or adds a new field. Expression categories: Struct. Declared arguments. Expression: Expression to update struct field with. Expression<AnyType> Locator: Locate inner elements with multiple entries like ['author', 'email']. StructLocator. Struct: The struct to update. Expression<Struct> Output type: Struct. Examples. Example 1: Base case. Argument values: Expression: value. Locator: flight. Struct: struct. structvalueOutput { airline: { id: NA, }, } foo. { airline: { id: NA, }, flight: foo, } Example 2: Base case. Argument values: Expression: value. Locator: flight. Struct: struct. structvalueOutput { airline: { id: FE, }, } { id: 1, } { airline: { id: FE, }, flight: { id: 1, }, } Example 3: Base case. Argument values: Expression: value. Locator: airline.id. Struct: struct. structvalueOutput { airline: { id: NA, }, } 1. { airline: { id: 1, }, } { airline: { id: FE, }, } 2. { airline: { id: 2, }, } Example 4: Null case. Argument values: Expression: value. Locator: airline.id. Struct: struct. structvalueOutput null. null. null. null. 1. null. { airline: { id: FE, }, } null. { airline: { id: null, }, }
