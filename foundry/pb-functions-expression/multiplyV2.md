---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/multiplyV2/"
title: "Multiply numbers"
---
# Multiply numbers

Supported in: Batch, Faster, Streaming. Calculates the product of all input columns. Expression categories: Numeric. Declared arguments. Expressions: List of columns to be multiplied. List<Expression<Numeric>> Output type: Numeric. Examples. Example 1: Base case. Argument values: Expressions: [col_a, col_b, col_c] col_acol_bcol_cOutput 10. 2. 3. 60. Example 2: Null case. Argument values: Expressions: [col_a, col_b] col_acol_bOutput null. null. null. Example 3: Null case. Argument values: Expressions: [col_a, col_b] col_acol_bOutput 1. null. null. Example 4: Null case. Argument values: Expressions: [col_a, col_b] col_acol_bOutput null. 1. null.
