---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/manuallyEnteredTableV1/"
title: "Manually entered table"
---
# Manually entered table

Supported in: Batch, Faster, Streaming. Uses manually entered table data to create an output. Transform categories: Other. Declared arguments. Rows: A list of structs representing rows, with struct fields representing column names and values. List<Literal<Struct>> optional Schema: A schema to be used if present for column names and types. If undefined, rows must be nonempty and will be used to infer the schema. Type<Struct> Examples. Example 1: Base case. Argument values: Rows: [{ airline: foundry airlines, flight_code: 112, flight_number: XB-123, }, { airline: foundry airlines, flight_code: 533, flight_number: MT-444, }, { airline: new air, flight_code: 934, flight_number: KK-123, }] Schema: Struct<flight_code, flight_number, airline> Inputs: Output: flight_codeflight_numberairline 112. XB-123. foundry airlines. 533. MT-444. foundry airlines. 934. KK-123. new air.
