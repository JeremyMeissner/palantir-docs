---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/lagV1/"
parquet_url: "/foundry/pb-functions-expression/lagV1/"
title: "Lag"
fetched_at: "2026-05-12T19:34:36.686Z"
---
Lag. Supported in: Batch, Faster. Returns the value of the input at 'lag' before the current row in the window. Expression categories: Aggregate. Declared arguments. Expression: Expression to lag. Expression<T> optional Default value: Default value if there is less than offset rows before the current row. Literal<T> optional Lag: Number of rows to lag. Literal<Integer> Type variable bounds: T accepts AnyType. Output type: T.
