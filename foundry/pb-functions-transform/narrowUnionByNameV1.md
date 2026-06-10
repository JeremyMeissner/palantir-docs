---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/narrowUnionByNameV1/"
parquet_url: "/foundry/pb-functions-transform/narrowUnionByNameV1/"
title: "Narrow union by name"
fetched_at: "2026-05-12T19:34:35.835Z"
---
Narrow union by name. Supported in: Batch, Faster. Unions a set of datasets together on the intersection of their column names, columns that are not present in all input datasets are removed. Transform categories: Join. Declared arguments. Datasets to union: The datasets being unioned together. List<Table> Examples. Example 1: Base case. Argument values: Datasets to union: [ri.foundry.main.dataset.a, ri.foundry.main.dataset.b] Inputs: ri.foundry.main.dataset.a. recently_servicedtail_number true. KK-150. false. XB-120. true. MT-190. ri.foundry.main.dataset.b. recently_servicedtail_numberairline_code true. AA-200. AA. true. BN-435. BN. true. BN-111. BN. Output: recently_servicedtail_number true. KK-150. false. XB-120. true. MT-190. true. AA-200. true. BN-435. true. BN-111.
