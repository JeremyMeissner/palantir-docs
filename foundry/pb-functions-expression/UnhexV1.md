---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/UnhexV1/"
title: "Convert from hexadecimal"
---
# Convert from hexadecimal

Supported in: Batch, Faster. Inverse of hex. Interprets each pair of characters as a hexadecimal number and converts to the byte representation of the number. Expression categories: Numeric, String. Declared arguments. Expression: String column to unhex. Expression<String> Output type: Binary. Examples. Example 1: Base case. Argument values: Expression: string_hex. string_hexOutput 68656C6C6F. aGVsbG8= 3039. MDk= FFFFFFFFFFFFCFC7. ////////z8c= 4C6F6E646F6E. TG9uZG9u. Example 2: Null case. Argument values: Expression: null. Output: null.
