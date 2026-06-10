---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/convertBaseV1/"
title: "Convert base"
---
# Convert base

Supported in: Batch, Streaming. Convert a number (or it string representation) from one base to another. Expression categories: Binary, Cast, Numeric. Declared arguments. Expression: Column to convert base. Expression<Byte | Integer | Long | Short | String> From base: Convert from base. Literal<Integer> To base: Convert to base. Literal<Integer> Output type: String. Examples. Example 1: Base case. Argument values: Expression: 4A801. From base: 16. To base: 10. Output: 305153. Example 2: Base case. Argument values: Expression: 8. From base: 10. To base: 2. Output: 1000. Example 3: Null case. Argument values: Expression: input. From base: 10. To base: 16. inputOutput null. null. Example 4: Edge case. Description: When input is made of characters that are outside the base of the given 'from base', only the leading characters up to the first out of base character is considered. Argument values: Expression: input. From base: 2. To base: 10. inputOutput 123. 1. 213. 0. 1032. 2.
