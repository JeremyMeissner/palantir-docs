---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/uuidV1/"
parquet_url: "/foundry/pb-functions-expression/uuidV1/"
title: "Universally unique identifier (uuid) (unstable)"
fetched_at: "2026-05-12T19:34:36.762Z"
---
Universally unique identifier (uuid) (unstable). Supported in: Batch, Faster, Streaming. Returns a column of UUID. This is not deterministic and will not produce the same result on repeated builds. This is not the preferred way to build an id column and users should look into SHA-256 or others that are deterministic, for example UUID v5. Expression categories: String. Declared arguments. This function does not take any arguments. Output type: String. Examples. Example 1: Base case. Description: Generate a column of UUID values (V4). Argument values: Output: 5c5622fe-e30e-4491-99b6-6213be506dec.
