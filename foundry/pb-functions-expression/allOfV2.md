---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/allOfV2/"
title: "Documentation | Pipeline Builder Expressions > All of"
---
# All of

> Supported in: Batch, Faster

Calculate the boolean 'and' of an aggregate, using SQL standard semantics for null values.

**Expression categories:** Aggregate

## Declared arguments

* **Expression:** The column on which to compute 'all'.<br>*Expression\<Boolean>*

**Output type:** *Boolean*

## Examples

### Example 1: Base case

**Argument values:**

* **Expression:** `values`

**Given input table:**

| values |
| ----- |
| true |
| false |
| true |

**Outputs:** false

***

### Example 2: Null case

**Argument values:**

* **Expression:** `values`

**Given input table:**

| values |
| ----- |
| *null* |
| *null* |

**Outputs:** *null*

***

### Example 3: Null case

**Argument values:**

* **Expression:** `values`

**Given input table:**

| values |
| ----- |
| true |
| true |
| *null* |

**Outputs:** true

***
