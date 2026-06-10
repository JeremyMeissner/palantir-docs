---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/unicodeNormalizeV1/"
parquet_url: "/foundry/pb-functions-expression/unicodeNormalizeV1/"
title: "Unicode normalize"
fetched_at: "2026-05-12T19:34:36.667Z"
---
Unicode normalize. Supported in: Batch, Faster, Streaming. Perform unicode normalization as per Unicode Standard Annex #15. Expression categories: Data preparation, String. Declared arguments. Expression: no description Expression<String> Normalization form: no description Enum<NFC, NFD, NFKC, NFKD> Output type: String. Examples. Example 1: Base case. Argument values: Expression: string. Normalization form: nfc. stringOutput １２３. １２３. イナゴ. イナゴ. Example 2: Base case. Argument values: Expression: string. Normalization form: nfd. stringOutput １２３. １２３. イナゴ. イナゴ. Example 3: Base case. Argument values: Expression: string. Normalization form: nfkc. stringOutput １２３. 123. イナゴ. イナゴ. Example 4: Base case. Argument values: Expression: string. Normalization form: nfkd. stringOutput １２３. 123. イナゴ. イナゴ.
