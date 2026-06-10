---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/decodeV1/"
parquet_url: "/foundry/pb-functions-expression/decodeV1/"
title: "Decode"
fetched_at: "2026-05-12T19:34:36.649Z"
---
Decode. Supported in: Batch, Faster, Streaming. Decode the given expression using the specified charset. Expression categories: Binary, Cast. Declared arguments. Charset: Charset used for decoding. Enum<ISO_8859_1, US_ASCII, UTF_16, UTF_16BE, UTF_16LE, UTF_8, Windows-31J> Expression: Expression to decode. Expression<Binary> Output type: String. Examples. Example 1: Base case. Argument values: Charset: UTF_16. Expression: city. cityOutput /v8ATABvAG4AZABvAG4= London. /v8AQwBvAHAAZQBuAGgAYQBnAGUAbg== Copenhagen. /v8ATgBlAHcAIABZAG8AcgBr. New York. Example 2: Base case. Argument values: Charset: UTF_8. Expression: city. cityOutput TG9uZG9u. London. Q29wZW5oYWdlbg== Copenhagen. TmV3IFlvcms= New York. Example 3: Null case. Argument values: Charset: UTF_8. Expression: city. cityOutput null. null.
