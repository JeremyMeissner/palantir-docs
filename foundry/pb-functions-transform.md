---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/"
title: "Documentation | Pipeline Builder Transforms > Aggregate"
---
# Aggregate

> Supported in: Batch, Faster

Performs the specified aggregations on the input dataset grouped by a set of columns.

**Transform categories**: Aggregate, Popular

## Declared arguments

* **Aggregations:** List of aggregations to perform on the dataset.<br>*List\<Expression\<AnyType>>*
* **Dataset:** Dataset to perform aggregate on.<br>*Table*
* *optional* **Group by columns:** List of columns to group the dataset by when aggregating. If empty, no group by is applied.<br>*List\<Column\<AnyType>>*

## Examples

### Example 1: Base case

**Argument values:**

* **Aggregations:** \[<br>alias(<br> alias: factor,<br> expression: <br>sum(<br> expression: `factor`,<br>),<br>)]
* **Dataset:** ri.foundry.main.dataset.aggregate
* **Group by columns:** \[`tail_number`]

**Input:**

| tail\_number | airline | miles | factor |
| ----- | ----- | ----- | ----- |
| XB-123 | foundry air | 124 | 2 |
| MT-222 | new airline | 1123 | 5 |
| XB-123 | foundry airline | 335 | 5 |
| MT-222 | new air | 565 | 4 |
| KK-452 | new air | 222 | 1 |
| XB-123 | foundry airline | 1134 | 3 |

**Output:**

| tail\_number | factor |
| ----- | ----- |
| XB-123 | 10 |
| MT-222 | 9 |
| KK-452 | 1 |

***
