---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/rowSizeV1/"
parquet_url: "/foundry/pb-functions-transform/rowSizeV1/"
title: "Row size"
fetched_at: "2026-05-12T19:34:35.863Z"
---
Row size. Supported in: Batch. Estimates the size of a single row in the JVM. Transform categories: Other. Declared arguments. Dataset: Dataset to calculate size of an individual row. Table. optional Row size column alias: Name of the column for the row estimate size value in bytes, defaults to 'size'. Literal<String> Examples. Example 1: Base case. Argument values: Dataset: ri.foundry.main.dataset.a. Row size column alias: size. Input: a 1. Output: asize 1. 16.
