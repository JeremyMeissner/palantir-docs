---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/renameColumnsV1/"
parquet_url: "/foundry/pb-functions-transform/renameColumnsV1/"
title: "Rename columns"
fetched_at: "2026-05-12T19:34:35.835Z"
---
Rename columns. Supported in: Batch, Faster, Streaming. Renames a set of columns. Transform categories: Data preparation, Popular. Declared arguments. Input dataset: Source dataset containing columns to be renamed. Table. Renames: Renames from existing column names to new names. List<Tuple<Column<AnyType>, Literal<String>>> Examples. Example 1: Base case. Argument values: Input dataset: ri.foundry.main.dataset.a. Renames: [(recently_serviced, does_not_require_service)] Input: recently_servicedtail_numberairline_code true. KK-150. KK. false. XB-120. XB. true. MT-190. MT. Output: does_not_require_servicetail_numberairline_code true. KK-150. KK. false. XB-120. XB. true. MT-190. MT.
