---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/sampleCovarianceV1/"
parquet_url: "/foundry/pb-functions-expression/sampleCovarianceV1/"
title: "Sample covariance"
fetched_at: "2026-05-12T19:34:36.611Z"
---
Sample covariance. Supported in: Batch, Streaming. Calculate the sample covariance of values in two columns. Expression categories: Aggregate. Declared arguments. Left: The first column on which we compute covariance. Expression<Numeric> Right: The second column on which we compute covariance. Expression<Numeric> Output type: Double. Examples. Example 1: Base case. Argument values: Left: left. Right: right. Given input table: leftright 1. 5. 2. 4. 3. 3. 4. 2. 5. 1. Outputs: -2.5. Example 2: Null case. Argument values: Left: left. Right: right. Given input table: leftright 1.0. 2.0. null. null. 2.0. 1.0. Outputs: -0.5.
