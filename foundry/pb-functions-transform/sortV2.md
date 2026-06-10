---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/sortV2/"
parquet_url: "/foundry/pb-functions-transform/sortV2/"
title: "Sort"
fetched_at: "2026-05-12T19:34:35.855Z"
---
Sort. Supported in: Batch, Faster. Transforms input dataset either by selecting columns or applying functions to columns. Transform categories: Other. Declared arguments. Dataset: Dataset to sort. Table. Sort specification: Specification for how to sort the dataset. List<Tuple<Column<ComparableType>, Enum<Ascending, Descending>>> Examples. Example 1: Base case. Argument values: Dataset: ri.foundry.main.dataset.a. Sort specification: [(b, DESCENDING)] Input: ab 1. 2. 3. 4. 5. 6. Output: ab 5. 6. 3. 4. 1. 2.
