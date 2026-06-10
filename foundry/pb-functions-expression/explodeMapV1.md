---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/explodeMapV1/"
parquet_url: "/foundry/pb-functions-expression/explodeMapV1/"
title: "Explode map"
fetched_at: "2026-05-12T19:34:36.639Z"
---
Explode map. Supported in: Batch, Streaming. Explode map into a row per key, value pair. Expression categories: Map. Declared arguments. Expression: The map to explode. Expression<Map<TKey, TValue>> Type variable bounds: TKey accepts AnyType**TValue accepts AnyType. Output type: Struct<Optional[key], Optional[value]> Examples. Example 1: Base case. Argument values: Expression: map. Given input table: map { 1 -> val1, 2 -> val2, } { 3 -> val3, 4 -> val4, } Expected output table: | map | | ----- | | { key -> 1, value -> val1, } | | { key -> 2, value -> val2, } | | { key -> 3, value -> val3, } | | { key -> 4, value -> val4, } | Example 2: Edge case. Argument values: Expression: map. Given input table: map { k1 -> q1, } { } Expected output table: | map | | ----- | | { key -> k1, value -> q1, } | Example 3: Edge case. Argument values: Expression: map. Given input table: map null. Expected output table: | map | | ----- |
