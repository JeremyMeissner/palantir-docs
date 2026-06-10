---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/urlEncodeV1/"
parquet_url: "/foundry/pb-functions-expression/urlEncodeV1/"
title: "Url encode"
fetched_at: "2026-05-12T19:34:36.667Z"
---
Url encode. Supported in: Batch, Faster, Streaming. Percent-encodes a string to be sent in a url. Expression categories: String. Declared arguments. Expression: The expression to url encode. Expression<String> Output type: String. Examples. Example 1: Base case. Argument values: Expression: string. stringOutput raw_string_with_no_special_characters. raw_string_with_no_special_characters. test/api?string=3. test%2Fapi%3Fstring%3D3. Example 2: Null case. Argument values: Expression: null. Output: null.
