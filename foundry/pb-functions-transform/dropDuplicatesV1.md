---
source_url: "https://www.palantir.com/docs/foundry/pb-functions-transform/dropDuplicatesV1/"
title: "Drop duplicates"
---
# Drop duplicates

Supported in: Batch, Faster. Drops duplicate rows from the input. Transform categories: Other. Declared arguments. Dataset: Dataset to deduplicate rows. Table. optional Column subset: If any columns are specified only those will be used when determining uniqueness. Set<Column<AnyType>> Examples. Example 1: Base case. Argument values: Dataset: ri.foundry.main.dataset.aggregate. Column subset: {tail_number} Input: tail_numberairlinemilesfactor XB-123. foundry air. 124. 2. MT-222. new airline. 1123. 5. XB-123. foundry airline. 335. 5. MT-222. new air. 565. 4. KK-452. new air. 222. 1. XB-123. foundry airline. 1134. 3. Output: tail_numberairlinemilesfactor XB-123. foundry air. 124. 2. MT-222. new airline. 1123. 5. KK-452. new air. 222. 1. Example 2: Base case. Description: No subset looks for exact duplicates. Argument values: Dataset: ri.foundry.main.dataset.aggregate. Column subset: {} Input: tail_numberairlinemilesfactor XB-123. foundry air. 124. 2. XB-123. foundry air. 124. 2. XB-123. foundry air. 124. 2. MT-222. new airline. 1123. 5. MT-222. new airline. 1123. 5. Output: tail_numberairlinemilesfactor XB-123. foundry air. 124. 2. MT-222. new airline. 1123. 5.
