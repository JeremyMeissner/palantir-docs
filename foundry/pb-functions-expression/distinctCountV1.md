---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/distinctCountV1/"
title: "Distinct count"
---
# Distinct count

Supported in: Batch, Faster, Streaming. Calculate distinct number of values in column. Expression categories: Aggregate. Declared arguments. Expression: The column of on which distinct count is computed. Expression<ComparableType> Output type: Long. Examples. Example 1: Base case. Argument values: Expression: values. Given input table: values 2. 4. 3. Outputs: 3. Example 2: Null case. Argument values: Expression: values. Given input table: values 2. 2. null. Outputs: 1.
