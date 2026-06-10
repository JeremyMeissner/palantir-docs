---
source_url: "https://www.palantir.com/docs/foundry/building-pipelines/create-incremental-syncs/"
parquet_url: "/foundry/building-pipelines/create-incremental-syncs/"
title: "Creating incremental syncs"
fetched_at: "2026-05-12T19:34:36.815Z"
---
Creating incremental syncs. Although it is possible to derive APPEND-only datasets in a pipeline from Data Connection syncs that are configured as SNAPSHOT transactions, most of the benefits of incremental pipelines come from applying incremental end-to-end. This means that data syncs into Foundry should consist of APPEND transactions that only bring new data into the system. An added benefit of configuring incremental syncs is that they minimize load on the source system and can reduce data storage requirements. Most datasets synced from source systems consist of files synced from a file system, or extracts from a database or data warehouse configured using a JDBC source type. The following guides walk you through how to configure incremental syncs for these source types: Optimize file-based append syncs. Incremental JDBC syncs.
