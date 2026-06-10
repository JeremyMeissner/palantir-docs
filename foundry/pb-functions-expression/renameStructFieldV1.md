---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/renameStructFieldV1/"
title: "Rename struct field"
---
# Rename struct field

Supported in: Batch, Faster, Streaming. Rename fields within a struct. Expression categories: Data preparation, Struct. Declared arguments. Expression: no description Expression<Struct> Renames: no description List<Tuple<StructLocator, Literal<String>>> Output type: Struct. Examples. Example 1: Base case. Argument values: Expression: struct. Renames: [(airline.id, identifier)] structOutput { airline: { id: NA, }, } { airline: { identifier: NA, }, } { airline: { id: FE, }, } { airline: { identifier: FE, }, } Example 2: Base case. Argument values: Expression: struct. Renames: [(airline.id, identifier)] structOutput null. null.
