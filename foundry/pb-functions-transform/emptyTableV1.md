---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/emptyTableV1/"
parquet_url: "/foundry/pb-functions-transform/emptyTableV1/"
title: "Empty table"
fetched_at: "2026-05-12T19:34:35.846Z"
---
Empty table. Supported in: Batch, Faster, Streaming. Creates an empty table with the given schema and read mode. Transform categories: Other. Declared arguments. Schema: A schema to be used for the output contract. Type<Struct> optional Read mode: The read mode of the empty dataset. Enum<INCREMENTAL, SNAPSHOT, STREAM, UNKNOWN> Examples. Example 1: Base case. Argument values: Schema: Struct<flight_code, flight_number, airline> Read mode: null. Inputs: Output: flight_codeflight_numberairline.
