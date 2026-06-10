---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-expression/normalRandomV1/"
parquet_url: "/foundry/pb-functions-expression/normalRandomV1/"
title: "Normal random number"
fetched_at: "2026-05-12T19:34:36.587Z"
---
Normal random number. Supported in: Batch, Faster, Streaming. Returns a column of normally distributed random numbers with zero mean and unit variance. This is not deterministic and will not produce the same result on repeated builds, even when using a seed. Expression categories: Numeric. Declared arguments. optional Seed: Adding a seed means that the random numbers will be generated from same sequence at each build. If you want true random numbers this should not be supplied. A seed will not produce fully deterministic results since compute may run distributed and the order in which random numbers are pulled for rows is not guaranteed. Literal<Long> Output type: Double.
