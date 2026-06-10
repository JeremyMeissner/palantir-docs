---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/addOrUpdateMapEntryV1/"
title: "Add or update map"
---
# Add or update map

Supported in: Batch, Streaming. Updates a value by key in a map or adds new key value pair. Expression categories: Map. Declared arguments. Expression: Expression to set as value for the key. Expression<V> Key: Key to add or update. Expression<K> Map: Map expression. Expression<Map<K, V>> Type variable bounds: K accepts AnyType**V accepts AnyType. Output type: Map<K, V> Examples. Example 1: Base case. Argument values: Expression: 4. Key: k. Map: map_col. map_colOutput { a -> 1, b -> 2, } { a -> 1, b -> 2, k -> 4, } Example 2: Base case. Argument values: Expression: 4. Key: k. Map: map_col. map_colOutput { a -> 1, b -> 2, k -> 2, } { a -> 1, b -> 2, k -> 4, } { a -> 1, b -> 2, } { a -> 1, b -> 2, k -> 4, } Example 3: Base case. Argument values: Expression: 4. Key: k. Map: map_col. map_colOutput { a -> 1, b -> 2, k -> 2, } { a -> 1, b -> 2, k -> 4, } Example 4: Null case. Argument values: Expression: 4. Key: null. Map: map_col. map_colOutput { a -> 1, } { a -> 1, } Example 5: Null case. Argument values: Expression: 4. Key: k. Map: map_col. map_colOutput null. null.
