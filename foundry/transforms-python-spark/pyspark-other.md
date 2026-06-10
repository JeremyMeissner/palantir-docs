---
source_url: "https://www.palantir.com/docs/foundry/transforms-python-spark/pyspark-other/"
parquet_url: "/foundry/transforms-python-spark/pyspark-other/"
title: "Other"
fetched_at: "2026-05-12T19:34:36.924Z"
---
Other. Collections. array(*cols). array_contains(col, value). size(col). sort_array(col, asc=True). struct(*cols). Sorting. asc(col). desc(col). Binary. bitwiseNOT(col). shiftLeft(col, numBits). shiftRight(col, numBits). shiftRightUnsigned(col, numBits). Dealing with null values. coalesce(*cols). isnan(col). isnull(col). Columns. col(col) or column(col). create_map(*cols). explode(col). expr(str). hash(*cols). input_file_name(). posexplode(col). sha1(col). sha2(col, numBits). soundex(col). spark_partition_id(). JSON. from_json(col, schema, options={}). get_json_object(col, path). json_tuple(col, *fields). to_json(col, options={}). Checkpoints. checkpoint(eager=True). localCheckpoint(eager=True). The checkpoint() function is used to temporarily store a DataFrame on disk, whereas localCheckpoint() stores them in executor memory. Use the eager parameter value to set whether or not the DataFrame is checkpointed immediately (default value is True).
