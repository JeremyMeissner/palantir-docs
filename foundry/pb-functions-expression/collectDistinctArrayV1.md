---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/collectDistinctArrayV1/"
parquet_url: "/foundry/pb-functions-expression/collectDistinctArrayV1/"
title: "Collect distinct array"
fetched_at: "2026-05-12T19:34:36.757Z"
---
Collect distinct array. Supported in: Batch, Faster, Streaming. Collects an array of deduplicated values within each group. Null values are ignored. Expression categories: Aggregate. Declared arguments. Expression: The column of values to collect into an array, keeping distinct values only. Expression<T> Type variable bounds: T accepts ComparableType. Output type: Array<T> Examples. Example 1: Base case. Argument values: Expression: factor. Given input table: factor 2. 2. 3. Outputs: [ 2, 3 ] Example 2: Null case. Argument values: Expression: factor. Given input table: factor 2. null. 3. Outputs: [ 2, 3 ]
