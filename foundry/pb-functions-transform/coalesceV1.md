---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/coalesceV1/"
parquet_url: "/foundry/pb-functions-transform/coalesceV1/"
title: "Coalesce data"
fetched_at: "2026-05-12T19:34:35.846Z"
---
Coalesce data. Supported in: Batch, Faster. Operation to reduce the number of partitions. If you have 1000 partitions and you coalesce to 100 there will not be a shuffle, instead each of the 100 new partitions will claim 10 of the current partitions. If a larger number of partitions is requested, it will stay at the current number of partitions. Transform categories: Other. Declared arguments. Dataset: Dataset to perform coalesce on. Table. Number of partitions: Number of partitions to coalesce to. Literal<Integer>
