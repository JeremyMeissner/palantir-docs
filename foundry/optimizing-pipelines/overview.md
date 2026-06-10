---
source_url: "https://www.palantir.com/docs/foundry/optimizing-pipelines/overview/"
parquet_url: "/foundry/optimizing-pipelines/overview/"
title: "Optimizing pipelines"
fetched_at: "2026-05-12T19:34:35.944Z"
---
Optimizing pipelines. In the course of creating data pipelines in Foundry, you may run into cases where it is necessary to understand the details of how computation works behind the scenes in order to effectively debug job failures or improve compute performance. In general, you should follow these steps when you encounter unexpected compute issues or performance problems. Note that if your pipeline is a batch pipeline, you may be able to speed up some compute jobs by making better use of the Spark engine that underlies computation in Foundry. However, this sort of performance tuning has limits. If your pipeline inputs are growing rapidly over time, you may need to adapt your pipeline to be incremental instead, to only process the rows or files of data that are actually changing. If you want to start by debugging a job or end-to-end pipeline that is failing unexpectedly, refer to these guides: Debug a failing job. Debug a failing pipeline. If you are interested in understanding how computation works in Foundry under the hood, begin by exploring the Spark core concepts.
