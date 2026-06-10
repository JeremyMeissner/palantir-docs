---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/HexV1/"
title: "Convert to hexadecimal"
---
# Convert to hexadecimal

Supported in: Batch, Faster, Streaming. Computes hex value of given expression. Expression categories: Numeric, String. Declared arguments. Expression: Column to hex. Expression<Binary | Byte | Integer | Long | Short | String> Output type: String. Examples. Example 1: Base case. Argument values: Expression: city_hex. city_hexOutput TG9uZG9u. 4C6F6E646F6E. Example 2: Base case. Argument values: Expression: -12345. Output: FFFFFFFFFFFFCFC7. Example 3: Base case. Argument values: Expression: 12345. Output: 3039. Example 4: Base case. Argument values: Expression: hello. Output: 68656C6C6F. Example 5: Null case. Argument values: Expression: null. Output: null.
