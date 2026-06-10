---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/projectV1/"
parquet_url: "/foundry/pb-functions-transform/projectV1/"
title: "Apply multiple expressions"
fetched_at: "2026-05-12T19:34:35.862Z"
---
Apply multiple expressions. Supported in: Batch, Faster, Streaming. Transforms input dataset either by selecting columns or applying functions to columns. Transform categories: Popular. Declared arguments. Columns: List of column transformations to apply to the dataset. List<Expression<AnyType>> Dataset: Dataset to apply operations to. Table. Keep remaining columns: Keeps all columns not projected in the dataset. Literal<Boolean> Examples. Example 1: Base case. Argument values: Columns: [ alias( alias: airline, expression: airline, )] Dataset: ri.foundry.main.dataset.a. Keep remaining columns: false. Input: airlinemiles foundry airways. 2500. new air. 3000. Output: airline foundry airways. new air. Example 2: Edge case. Argument values: Columns: [ alias( alias: media_column, expression: media_ref, )] Dataset: ri.foundry.main.dataset.a. Keep remaining columns: false. Input: pk 1. Output: media_column media_ref.
