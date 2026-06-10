---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/isValidMgrsV1/"
parquet_url: "/foundry/pb-functions-expression/isValidMgrsV1/"
title: "Is valid MGRS"
fetched_at: "2026-05-12T19:34:36.739Z"
---
Is valid MGRS. Supported in: Batch, Faster, Streaming. Returns true if the input is a valid MGRS (military grid reference system) string. Expression categories: Geospatial. Declared arguments. Expression: String following an MGRS (military grid reference system) format. Expression<String> Output type: Boolean. Examples. Example 1: Base case. Argument values: Expression: mgrs. mgrsOutput not an mgrs value. false. 4Q FJ. false. 1 6. false. 4Q. false. 4Q FJ 1. false. Example 2: Base case. Argument values: Expression: mgrs. mgrsOutput 4Q FJ 1 6. true. 4Q FJ 12345 67890. true. Example 3: Null case. Argument values: Expression: mgrs. mgrsOutput null. false.
