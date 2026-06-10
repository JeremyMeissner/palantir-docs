---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/extractMapKeysV1/"
parquet_url: "/foundry/pb-functions-expression/extractMapKeysV1/"
title: "Extract map keys"
fetched_at: "2026-05-12T19:34:36.692Z"
---
Extract map keys. Supported in: Batch, Faster, Streaming. Return map keys as an array. Note the order of array elements is not deterministic. Expression categories: Map. Declared arguments. Map: Map expression. Expression<Map<K, AnyType>> Type variable bounds: K accepts AnyType. Output type: Array<K> Examples. Example 1: Base case. Argument values: Map: flight_number. flight_numberOutput { MT-111 -> 2, XB-134 -> 1, } [ XB-134, MT-111 ] Example 2: Null case. Argument values: Map: flight_number. flight_numberOutput null. null.
