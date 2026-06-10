---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/valueFromMapV1/"
title: "Value from map"
---
# Value from map

Supported in: Batch, Faster, Streaming. Get a value from a map using a key. Expression categories: Map. Declared arguments. Key: Key expression. Expression<K> Map: Map expression. Expression<Map<K, V>> Type variable bounds: K accepts ComparableType**V accepts AnyType. Output type: V. Examples. Example 1: Base case. Argument values: Key: [ 1 ] Map: { [ 1 ] -> Foo, } Output: Foo. Example 2: Base case. Argument values: Key: Bar. Map: { Bar -> 2, Foo -> 1, } Output: 2. Example 3: Base case. Argument values: Key: 1. Map: { 1 -> 10, 2 -> 20, } Output: 10. Example 4: Base case. Argument values: Key: Foo. Map: { Bar -> World, Foo -> Hello, } Output: Hello. Example 5: Base case. Argument values: Key: Foo. Map: { Bar -> World, } Output: null. Example 6: Base case. Argument values: Key: [ [ 1 ], [ 1 ] ] Map: { [ [ 1 ], [ 1 ] ] -> Foo, } Output: Foo. Example 7: Null case. Argument values: Key: key. Map: map. mapkeyOutput null. null. null. { Foo -> Hello, } null. null. null. Foo. null.
