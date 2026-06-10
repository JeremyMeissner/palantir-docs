---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/andV1/"
title: "And"
---
# And

Supported in: Batch, Faster, Streaming. Returns true if all of the specified conditions are true. Nulls are considered false. Expression categories: Boolean. Declared arguments. Conditions: List of conditions from which the output is calculated. List<Expression<Boolean>> Output type: Boolean. Examples. Example 1: Base case. Argument values: Conditions: [left_boolean, right_boolean] left_booleanright_booleanOutput true. true. true. true. false. false. false. true. false. false. false. false. Example 2: Null case. Argument values: Conditions: [null, true] Output: false.
