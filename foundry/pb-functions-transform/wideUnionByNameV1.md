---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/wideUnionByNameV1/"
parquet_url: "/foundry/pb-functions-transform/wideUnionByNameV1/"
title: "Wide union by name"
fetched_at: "2026-05-12T19:34:35.849Z"
---
Wide union by name. Supported in: Batch, Faster, Streaming. Unions a set of datasets together on the superset of their column names, adding nulls when columns are missing. Transform categories: Join. Declared arguments. Datasets to union: The datasets being unioned together. List<Table> Examples. Example 1: Base case. Argument values: Datasets to union: [ri.foundry.main.dataset.a, ri.foundry.main.dataset.b] Inputs: ri.foundry.main.dataset.a. recently_servicedtail_number true. KK-150. false. XB-120. true. MT-190. ri.foundry.main.dataset.b. recently_servicedtail_numberairline_code true. AA-200. AA. true. BN-435. BN. true. BN-111. BN. Output: recently_servicedtail_numberairline_code true. KK-150. null. false. XB-120. null. true. MT-190. null. true. AA-200. AA. true. BN-435. BN. true. BN-111. BN.
