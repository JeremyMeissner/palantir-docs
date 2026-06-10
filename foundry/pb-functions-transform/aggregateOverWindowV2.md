---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/aggregateOverWindowV2/"
parquet_url: "/foundry/pb-functions-transform/aggregateOverWindowV2/"
title: "Aggregate over window"
fetched_at: "2026-05-12T19:34:35.860Z"
---
Aggregate over window. Supported in: Streaming. Performs the specified aggregations on the data within a window, emitting outputs as specified by the provided trigger. Transform categories: Aggregate. Declared arguments. Aggregate expressions: List of aggregate expressions to evaluate over each window. List<Expression<AnyType>> Dataset: Dataset to perform aggregations on. Table. Window: Window defining how elements should be grouped. Window. optional Accumulation mode: The accumulation mode for the window. Determines whether the window accumulates panes when the trigger fires or discards them. Enum<Accumulating, Discarding> optional Key by columns: Columns on which to partition the input by key. Each aggregation will be computed separately for each distinct key value. Set<Column<Binary | Boolean | Byte | Double | Float | Integer | Long | Short | String | Timestamp>> optional Trigger: Trigger defining when aggregation should be performed. Trigger.
