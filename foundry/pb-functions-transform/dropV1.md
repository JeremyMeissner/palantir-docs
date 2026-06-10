---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/dropV1/"
title: "Drop columns"
---
# Drop columns

Supported in: Batch, Faster, Streaming. Transforms input dataset by dropping the specified columns. Transform categories: Popular. Declared arguments. Columns to drop: List of columns to drop. Set<Column<AnyType>> Dataset: Dataset to drop columns from. Table. Examples. Example 1: Base case. Argument values: Columns to drop: {miles} Dataset: ri.foundry.main.dataset.a. Input: airlinemilesairports foundry airways. 3000. [ JFK, SFO ] Output: airlineairports foundry airways. [ JFK, SFO ]
