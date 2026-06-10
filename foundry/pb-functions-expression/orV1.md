---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/orV1/"
title: "Or"
---
# Or

Supported in: Batch, Faster, Streaming. Returns true if any of the specified conditions are true. Nulls are considered false. Expression categories: Boolean. Declared arguments. Conditions: List of conditions from which the output is calculated. List<Expression<Boolean>> Output type: Boolean. Examples. Example 1: Base case. Argument values: Conditions: [left_boolean, right_boolean] left_booleanright_booleanOutput true. true. true. true. false. true. false. true. true. false. false. false. Example 2: Null case. Argument values: Conditions: [null, true] Output: true.
