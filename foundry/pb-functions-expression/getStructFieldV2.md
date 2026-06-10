---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/getStructFieldV2/"
title: "Get struct field"
---
# Get struct field

Supported in: Batch, Faster, Streaming. Extracts a field from a struct. Expression categories: Struct. Declared arguments. Locator: Extract inner elements with multiple entries like ['author', 'email']. StructLocator. Struct: no description Expression<Struct> Output type: AnyType. Examples. Example 1: Base case. Argument values: Locator: airline.id. Struct: struct. structOutput { airline: { id: NA, }, } NA. { airline: { id: FE, }, } FE. Example 2: Base case. Argument values: Locator: airline.id. Struct: struct. structOutput { airline: null, } null. { airline: { id: null, }, } null. null. null.
