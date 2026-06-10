---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/isInV1/"
parquet_url: "/foundry/pb-functions-expression/isInV1/"
title: "Is in"
fetched_at: "2026-05-12T19:34:36.695Z"
---
Is in. Supported in: Batch, Faster, Streaming. Returns true if the list contains the value. Expression categories: Boolean. Declared arguments. Contains: The list to search within. List<Expression<T>> Value: The value to look for. Expression<T> Type variable bounds: T accepts ComparableType. Output type: Boolean. Examples. Example 1: Base case. Description: Elements can be arrays. Argument values: Contains: [one, two] Value: value. onetwovalueOutput [ 1 ] [ 2 ] [ 1 ] true. [ 1, 2 ] [ 2 ] [ 1 ] false. Example 2: Base case. Description: You can check if the list contains the value. Argument values: Contains: [AWE-112, BRR-123] Value: value. valueOutput BRR-123. true. ABC-543. false. Example 3: Base case. Description: Elements can be structs. Argument values: Contains: [one, two] Value: value. onetwovalueOutput { part: AWE-112, } { part: BRR-123, } { part: AWE-112, } true. { part: CSE-122, } { part: BRR-123, } { part: AWE-112, } false. Example 4: Null case. Description: You can check for null. Argument values: Contains: [one, two, three] Value: value. onetwothreevalueOutput 1. 2. 3. null. false. null. null. null. 1. false. 1. 2. null. null. true.
