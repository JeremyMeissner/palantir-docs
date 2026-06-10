---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/notAnyV1/"
parquet_url: "/foundry/pb-functions-expression/notAnyV1/"
title: "Not any"
fetched_at: "2026-05-12T19:34:36.753Z"
---
Not any. Supported in: Batch, Streaming. Returns true only if all of the specified conditions are false. Nulls are considered false. Expression categories: Boolean. Declared arguments. Conditions: List of conditions from which the output is calculated. List<Expression<Boolean>> Output type: Boolean. Examples. Example 1: Base case. Argument values: Conditions: [left_boolean, right_boolean] left_booleanright_booleanOutput true. true. false. true. false. false. false. true. false. false. false. true. Example 2: Null case. Argument values: Conditions: [null, null] Output: true. Example 3: Null case. Argument values: Conditions: [null, true] Output: false.
