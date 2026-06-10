---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/cbacStringToGroupNamesV3/"
parquet_url: "/foundry/pb-functions-expression/cbacStringToGroupNamesV3/"
title: "Parse classification string"
fetched_at: "2026-05-12T19:34:36.770Z"
---
Parse classification string. Supported in: Batch, Streaming. Returns the markings parsed from a given classification string. This output is formatted as a struct, where the first element of the struct is an array comprising the classification markings that represent the input. This list is null if the classification string is invalid, or if there are other errors that occur while parsing the markings. The second element of the struct is the string of error message(s). If there are no errors, the error field will be null. This expression is called asynchronously for performance. Expression categories: Other. Declared arguments. Expression: A classification string. Expression<String> Output type: Struct<markingIds<Classification>, errors> Examples. Example 1: Base case. Argument values: Expression: cbacString. cbacStringOutput MS//MNF. [ MS, MNF ] Example 2: Base case. Argument values: Expression: cbacString. cbacStringOutput empty string. [ ]
