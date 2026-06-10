---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/urlDecodeV1/"
parquet_url: "/foundry/pb-functions-expression/urlDecodeV1/"
title: "Url decode"
fetched_at: "2026-05-12T19:34:36.674Z"
---
Url decode. Supported in: Batch, Faster, Streaming. Decodes a percent-encoded string to plain text. Expression categories: Cast, String. Declared arguments. Expression: The expression to url decode. Expression<String> Output type: String. Examples. Example 1: Base case. Argument values: Expression: string. stringOutput raw_string_with_no_special_characters. raw_string_with_no_special_characters. test%2Fapi%3Fstring%3D3. test/api?string=3. Example 2: Null case. Argument values: Expression: null. Output: null.
