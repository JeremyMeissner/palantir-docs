---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/isNullV1/"
title: "Is null"
---
# Is null

Supported in: Batch, Faster, Streaming. Returns true if the input is null, can optionally treat empty strings as null. Expression categories: Boolean. Declared arguments. Expression: The expression to check for null values. Expression<AnyType> optional Treat empty strings as null: Whether to treat empty strings as null values. Literal<Boolean> Output type: Boolean. Examples. Example 1: Base case. Argument values: Expression: empty string. Treat empty strings as null: true. Output: true. Example 2: Base case. Argument values: Expression: hello. Treat empty strings as null: null. Output: false. Example 3: Base case. Argument values: Expression: 1. Treat empty strings as null: null. Output: false. Example 4: Base case. Argument values: Expression: null. Treat empty strings as null: null. Output: true.
