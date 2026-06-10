---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/getManyStructFieldsV1/"
title: "Extract many struct fields"
---
# Extract many struct fields

Supported in: Batch, Faster. Extracts many fields from a struct. Original struct will be dropped. Transform categories: Struct. Declared arguments. Dataset: Dataset containing struct column. Table. Locators: Locators for fields to access in the struct. List<Tuple<StructLocator, Literal<String>>> Struct: Input struct. Column<Struct> Examples. Example 1: Base case. Argument values: Dataset: ri.foundry.main.dataset.a. Locators: [(airline.name, airline), (tail_no, tail_number)] Struct: raw. Input: raw { airline: { id: NA, name: new air, }, tail_no: NA-123, } { airline: { id: FA, name: foundry airways, }, tail_no: FA-123, } Output: airlinetail_number new air. NA-123. foundry airways. FA-123.
