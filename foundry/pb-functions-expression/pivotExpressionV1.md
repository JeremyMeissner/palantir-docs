---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/pivotExpressionV1/"
title: "Pivot"
---
# Pivot

Supported in: Streaming. Apply an aggregate expression in a pivot context. The aggregation will run as a set of separate aggregations scoped to each distinct value of the pivot expression. The output is a map from pivot value to aggregate expression value. Expression categories: Aggregate. Declared arguments. Aggregate expression: The aggregate expression to apply. Expression<V> Pivot expression: The pivot expression to apply. Expression<K> Type variable bounds: K accepts ComparableType**V accepts AnyType. Output type: Map<K, V> Examples. Example 1: Base case. Argument values: Aggregate expression: sum( expression: value, ). Pivot expression: pivot. Given input table: pivotvalue a. 1. b. 2. a. 3. Outputs: { a -> 4, b -> 2, } Example 2: Base case. Argument values: Aggregate expression: sum( expression: value, ). Pivot expression: cleanString( cleanActions: {trim}, expression: pivot, ). Given input table: pivotvalue a. 1. b. 2. a. 3. Outputs: { a -> 4, b -> 2, }
