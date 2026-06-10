---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/sumV1/"
parquet_url: "/foundry/pb-functions-expression/sumV1/"
title: "Sum"
fetched_at: "2026-05-12T19:34:36.780Z"
---
Sum. Supported in: Batch, Faster, Streaming. Sums the specified expression. Expression categories: Numeric. Declared arguments. Expression: The column to be summed. Expression<Numeric> Output type: Decimal | Double | Long. Examples. Example 1: Base case. Argument values: Expression: values. Given input table: values 2. 4. 3. Outputs: 9. Example 2: Null case. Argument values: Expression: values. Given input table: values 2. null. 3. Outputs: 5. Example 3: Edge case. Argument values: Expression: values. Given input table: values 1.111111111111. 1.111111111111. Outputs: 2.222222222222.
