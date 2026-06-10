---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/removeMapEntryByKeyV1/"
parquet_url: "/foundry/pb-functions-expression/removeMapEntryByKeyV1/"
title: "Remove map entry by key"
fetched_at: "2026-05-12T19:34:36.744Z"
---
Remove map entry by key. Supported in: Batch, Streaming. Removes a map entry by the given key. Expression categories: Map. Declared arguments. Key: Key of the entry to remove. Expression<K> Map: Map expression. Expression<Map<K, V>> Type variable bounds: K accepts AnyType**V accepts AnyType. Output type: Map<K, V> Examples. Example 1: Base case. Argument values: Key: k. Map: map_col. map_colOutput { a -> 1, k -> 2, } { a -> 1, } Example 2: Base case. Argument values: Key: j. Map: map_col. map_colOutput { a -> 1, k -> 2, } { a -> 1, k -> 2, } Example 3: Null case. Argument values: Key: k. Map: map_col. map_colOutput null. null. Example 4: Null case. Argument values: Key: null. Map: map_col. map_colOutput { a -> foo, } { a -> foo, }
