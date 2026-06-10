---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/allOfV1/"
parquet_url: "/foundry/pb-functions-expression/allOfV1/"
title: "All of"
fetched_at: "2026-05-12T19:34:36.692Z"
---
All of. Supported in: Batch, Faster. Calculate the boolean 'and' of an aggregate. Nulls are considered false. Expression categories: Aggregate. Declared arguments. Expression: The column on which to compute 'all'. Expression<Boolean> Output type: Boolean. Examples. Example 1: Base case. Argument values: Expression: values. Given input table: values true. false. true. Outputs: false. Example 2: Null case. Argument values: Expression: values. Given input table: values true. true. null. Outputs: false.
