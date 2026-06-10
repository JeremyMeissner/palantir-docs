---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/dateSequenceV1/"
parquet_url: "/foundry/pb-functions-expression/dateSequenceV1/"
title: "Date sequence"
fetched_at: "2026-05-12T19:34:36.762Z"
---
Date sequence. Supported in: Batch, Faster. Creates an array with dates in range from start to end. Expression categories: Datetime. Declared arguments. End date: The date to end at (inclusive). Expression<Date> Start date: The date to start from (inclusive). Expression<Date> Step unit: Unit of the step size. Enum<Days, Months, Quarters, Weeks, Years> optional Step size: The size of the steps between numbers. Defaults to 1. Expression<Numeric> Output type: Array<Date> Examples. Example 1: Base case. Argument values: End date: last_planned_flight. Start date: first_planned_flight. Step unit: DAYS. Step size: null. first_planned_flightlast_planned_flightOutput 2023-01-01. 2023-01-03. [ 2023-01-01, 2023-01-02, 2023-01-03 ] 2023-01-31. 2023-02-02. [ 2023-01-31, 2023-02-01, 2023-02-02 ] 2023-02-28. 2023-03-01. [ 2023-02-28, 2023-03-01 ]
