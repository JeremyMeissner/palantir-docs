---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/rowCountV1/"
parquet_url: "/foundry/pb-functions-expression/rowCountV1/"
title: "Row count"
fetched_at: "2026-05-12T19:34:36.611Z"
---
Row count. Supported in: Batch, Faster, Streaming. Counts the number of non null rows in a group. Expression categories: Aggregate. Declared arguments. optional Expression: no description Expression<AnyType> Output type: Long. Examples. Example 1: Base case. Argument values: Expression: values. Given input table: values 2. 4. 3. Outputs: 3. Example 2: Null case. Argument values: Expression: values. Given input table: values 2. null. 3. Outputs: 2.
