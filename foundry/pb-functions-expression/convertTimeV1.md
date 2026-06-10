---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/convertTimeV1/"
parquet_url: "/foundry/pb-functions-expression/convertTimeV1/"
title: "Convert between time units"
fetched_at: "2026-05-12T19:34:36.707Z"
---
Convert between time units. Supported in: Batch, Faster, Streaming. Expression categories: Datetime. Declared arguments. Amount of current unit: no description Expression<DefiniteNumeric> Current unit: The unit prior to conversion. Enum<Days, Hours, Milliseconds, Minutes, Seconds, Weeks> Target unit: The desired unit after conversion. Enum<Days, Hours, Milliseconds, Minutes, Seconds, Weeks> Output type: Double. Examples. Example 1: Base case. Argument values: Amount of current unit: days. Current unit: days. Target unit: minutes. daysOutput 12. 17280.0. Example 2: Null case. Argument values: Amount of current unit: days. Current unit: days. Target unit: minutes. daysOutput null. null.
