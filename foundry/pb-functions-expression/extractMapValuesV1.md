---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/extractMapValuesV1/"
parquet_url: "/foundry/pb-functions-expression/extractMapValuesV1/"
title: "Extract map values"
fetched_at: "2026-05-12T19:34:36.770Z"
---
Extract map values. Supported in: Batch, Faster, Streaming. Return map values as an array. Note the order of array elements is not deterministic. Expression categories: Map. Declared arguments. Map: Map expression. Expression<Map<AnyType, V>> Type variable bounds: V accepts AnyType. Output type: Array<V> Examples. Example 1: Base case. Argument values: Map: flight_number. flight_numberOutput { MT-111 -> 2, XB-134 -> 1, } [ 1, 2 ] Example 2: Null case. Argument values: Map: flight_number. flight_numberOutput { MT-111 -> 2, XB-134 -> null, } [ null, 2 ] null. null.
