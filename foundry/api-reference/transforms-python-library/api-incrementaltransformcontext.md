---
source_url: "https://www.palantir.com/docs/foundry/api-reference/transforms-python-library/api-incrementaltransformcontext/"
title: "Documentation | transforms.api > IncrementalTransformContext"
---
# transforms.api.IncrementalTransformContext

## *class* transforms.api.IncrementalTransformContext(is\_incremental, snapshot\_inputs, \*args) {#transforms.api.IncrementalTransformContext}

[`TransformContext`](/docs/foundry/api-reference/transforms-python-library/api-transformcontext/#transforms.api.TransformContext) with added functionality for incremental computation.

### abort\_job() {#transforms.api.IncrementalTransformContext.abort\_job}

Aborts the job and ends execution. This will abort all output transactions.

#### History

* Added in version 1.7.0.

### *property* auth\_header {#transforms.api.IncrementalTransformContext.auth\_header}

The auth header used to run the transform.

* **Type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)

### *property* environment {#transforms.api.IncrementalTransformContext.environment}

The list of solved conda packages.

* **Type:**
  List\[[str ↗](https://docs.python.org/3/library/stdtypes.html#str)]

### *property* fallback\_branches {#transforms.api.IncrementalTransformContext.fallback\_branches}

The fallback branches configured when running the transform.

* **Type:**
  List\[[str ↗](https://docs.python.org/3/library/stdtypes.html#str)]

### *property* is\_incremental {#transforms.api.IncrementalTransformContext.is\_incremental}

If the transform is running incrementally.

* **Type:**
  [bool ↗](https://docs.python.org/3/library/functions.html#bool)

### *property* parameters {#transforms.api.IncrementalTransformContext.parameters}

Transform parameters.

* **Type:**
  [dict ↗](https://docs.python.org/3/library/stdtypes.html#dict) of ([str ↗](https://docs.python.org/3/library/stdtypes.html#str), any)

### *property* spark\_session {#transforms.api.IncrementalTransformContext.spark\_session}

The Spark session used to run the transform.

* **Type:**
  [pyspark.sql.SparkSession ↗](https://spark.apache.org/docs/latest/api/python/reference/pyspark.sql/api/pyspark.sql.SparkSession.html#pyspark.sql.SparkSession)
