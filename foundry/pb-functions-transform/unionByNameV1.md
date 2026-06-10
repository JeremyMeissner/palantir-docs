---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/unionByNameV1/"
parquet_url: "/foundry/pb-functions-transform/unionByNameV1/"
title: "Union by name"
fetched_at: "2026-05-12T19:34:35.862Z"
---
Union by name. Supported in: Batch, Faster, Streaming. Unions a set of datasets together on matching column names. Transform categories: Join. Declared arguments. Datasets to union: The datasets being unioned together. List<Table> Examples. Example 1: Base case. Argument values: Datasets to union: [ri.foundry.main.dataset.a, ri.foundry.main.dataset.b] Inputs: ri.foundry.main.dataset.a. recently_servicedtail_numberairline_code true. KK-150. KK. false. XB-120. XB. true. MT-190. MT. ri.foundry.main.dataset.b. recently_servicedtail_numberairline_code true. AA-200. AA. true. BN-435. BN. true. BN-111. BN. Output: recently_servicedtail_numberairline_code true. KK-150. KK. false. XB-120. XB. true. MT-190. MT. true. AA-200. AA. true. BN-435. BN. true. BN-111. BN.
