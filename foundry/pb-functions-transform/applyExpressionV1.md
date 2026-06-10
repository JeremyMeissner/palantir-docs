---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/applyExpressionV1/"
title: "Apply expression"
---
# Apply expression

Supported in: Batch, Faster, Streaming. Transforms input dataset by applying a single expression. Transform categories: Popular. Declared arguments. Dataset: Dataset to apply expression to. Table. Expression: Expression to apply. Expression<AnyType> Examples. Example 1: Base case. Argument values: Dataset: ri.foundry.main.dataset.a. Expression: alias( alias: kilometers, expression: convertDistance( amount: miles, currentUnit: mile, targetUnit: kilometer, ), ). Input: airlinemiles foundry airways. 2500. new air. 3000. Output: kilometersairlinemiles 4023.36. foundry airways. 2500. 4828.03. new air. 3000.
