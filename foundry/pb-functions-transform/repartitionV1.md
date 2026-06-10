---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/repartitionV1/"
title: "Repartition data"
---
# Repartition data

Supported in: Batch, Faster. Forces a shuffle of the data based on optionally provided partitioning columns and a resulting number of partitions. If these are not provided, the partitioning will be determined automatically. Transform categories: Other. Declared arguments. Dataset: Dataset to perform aggregate on. Table. optional Incremental partition count: Number of partitions to reshuffle to if the build is incrementally updated. Literal<Integer> optional Number of partitions: Number of partitions to reshuffle to. Literal<Integer> optional Partitioning columns: Specifies the list of columns to be used for repartitioning. List<Column<AnyType>>
