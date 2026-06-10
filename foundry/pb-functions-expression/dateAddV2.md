---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/dateAddV2/"
title: "Add value to date"
---
# Add value to date

Supported in: Batch, Faster, Streaming. Returns the date that is 'value' days/weeks/months/quarter/years after 'start'. Expression categories: Datetime. Declared arguments. Date: Date to add value to. Expression<Date> Unit: Date unit of the 'value' parameter. Enum<Days, Months, Quarters, Weeks, Years> Value: Number of days / weeks / quarters / years to add. Expression<Integer> Output type: Date. Examples. Example 1: Base case. Argument values: Date: 2022-02-01. Unit: DAYS. Value: 2. Output: 2022-02-03. Example 2: Base case. Argument values: Date: 2022-02-01. Unit: MONTHS. Value: 2. Output: 2022-04-01. Example 3: Base case. Argument values: Date: 2022-02-01. Unit: QUARTERS. Value: 2. Output: 2022-08-01. Example 4: Base case. Argument values: Date: 2022-02-01. Unit: YEARS. Value: 2. Output: 2024-02-01. Example 5: Null case. Argument values: Date: date. Unit: YEARS. Value: value. datevalueOutput 2022-02-01. null. null. null. 2. null. null. null. null.
