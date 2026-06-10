---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/UnhexToStringV1/"
title: "Convert from hexadecimal to string"
---
# Convert from hexadecimal to string

Supported in: Batch, Faster, Streaming. Inverse of hex, interprets each pair of characters as a hexadecimal number and converts to the utf-8 string of the byte representation of the number. Expression categories: String. Declared arguments. Expression: String column to unhex. Expression<String> Output type: String. Examples. Example 1: Base case. Argument values: Expression: string_hex. string_hexOutput 68656C6C6F. hello. 4C6F6E646F6E. London. Example 2: Null case. Argument values: Expression: null. string_hexOutput null. null.
