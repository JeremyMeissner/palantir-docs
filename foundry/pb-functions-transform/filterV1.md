---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/filterV1/"
parquet_url: "/foundry/pb-functions-transform/filterV1/"
title: "Filter"
fetched_at: "2026-05-12T19:34:35.828Z"
---
Filter. Supported in: Batch, Faster, Streaming. Filters the input dataset based on the specified filter condition. Transform categories: Data preparation, Popular. Declared arguments. Dataset: Dataset to filter. Table. Filter condition: Condition to filter on. Values that return true are kept, others are removed. Expression<Boolean> Examples. Example 1: Base case. Argument values: Dataset: ri.foundry.main.dataset.a. Filter condition: recently_serviced. Input: recently_servicedtail_number true. KK-150. false. XB-120. true. MT-190. Output: recently_servicedtail_number true. KK-150. true. MT-190. Example 2: Base case. Description: Nulls are treated as false. Argument values: Dataset: ri.foundry.main.dataset.a. Filter condition: recently_serviced. Input: recently_servicedtail_number null. KK-150. true. XB-120. Output: recently_servicedtail_number true. XB-120.
