---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/subtractManyV1/"
title: "Subtract multiple expressions"
---
# Subtract multiple expressions

Supported in: Batch, Faster, Streaming. Calculates the difference between a number and all input columns. Expression categories: Numeric. Declared arguments. Expressions list: List of expressions to be used for subtraction. List<Expression<Numeric>> Value to be subtracted: Expression to subtract from. Expression<Numeric> Output type: Numeric. Examples. Example 1: Base case. Argument values: Expressions list: [col_b, col_c] Value to be subtracted: col_a. col_acol_bcol_cOutput 5. 3. 2. 0. 2. 4. 0. -2. -2. -4. -2. 4. Example 2: Base case. Argument values: Expressions list: [col_b] Value to be subtracted: col_a. col_acol_bOutput null. null. null. 1. null. null. null. 10. null.
