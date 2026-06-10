---
source_url: "https://www.palantir.com/docs/foundry/api-reference/transforms-python-library/api-incrementaltransforminput/"
title: "Documentation | transforms.api > IncrementalTransformInput"
---
# transforms.api.IncrementalTransformInput

## *class* transforms.api.IncrementalTransformInput(tinput, prev\_txrid=None, batch\_end\_txrid=None) {#transforms.api.IncrementalTransformInput}

[`TransformInput`](/docs/foundry/api-reference/transforms-python-library/api-transforminput/#transforms.api.TransformInput) with added functionality for incremental computation.

### *property* batch\_incremental\_configuration {#transforms.api.IncrementalTransformInput.batch\_incremental\_configuration}

The configuration for an incremental input that will be read in batches.

* **Type:**
  `BatchIncrementalConfiguration`

#### History

* Added in version 1.7.0.

### *property* branch {#transforms.api.IncrementalTransformInput.branch}

The branch of the dataset.

* **Type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)

### *property* column\_descriptions {#transforms.api.IncrementalTransformInput.column\_descriptions}

The column descriptions of the dataset.

* **Type:**
  `Dict[str, str]`

### *property* column\_typeclasses {#transforms.api.IncrementalTransformInput.column\_typeclasses}

The column typeclasses of the dataset.

* **Type:**
  `Dict[str, str]`

### dataframe(mode='added') {#transforms.api.IncrementalTransformInput.dataframe}

Return a [`pyspark.sql.DataFrame` ↗](https://spark.apache.org/docs/latest/api/python/reference/pyspark.sql/api/pyspark.sql.DataFrame.html#pyspark.sql.DataFrame) for the given read mode.

Only current, previous and added modes are supported.

* **Parameters:**
  **mode** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – The read mode, one of current, previous, added, modified, or removed. Defaults to added.
* **Returns:**
  The DataFrame for the dataset.
* **Return type:**
  [`DataFrame` ↗](https://spark.apache.org/docs/latest/api/python/reference/pyspark.sql/api/pyspark.sql.DataFrame.html#pyspark.sql.DataFrame)

### *property* end\_transaction\_rid {#transforms.api.IncrementalTransformInput.end\_transaction\_rid}

The ending transaction of the input dataset.

* **Type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)

### filesystem(mode='added') {#transforms.api.IncrementalTransformInput.filesystem}

Construct a FileSystem object for reading from FoundryFS for the given read mode.

Only current, previous and added modes are supported.

* **Parameters:**
  **mode** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – The read mode, one of current, previous, added, modified, or removed. Defaults to added.
* **Returns:**
  A filesystem object for the given view.
* **Return type:**
  [`FileSystem`](/docs/foundry/api-reference/transforms-python-library/api-filesystem/#transforms.api.FileSystem)

### pandas() {#transforms.api.IncrementalTransformInput.pandas}

[`pandas.DataFrame` ↗](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html#pandas.DataFrame): A Pandas dataframe containing the full view of the dataset.

### *property* path {#transforms.api.IncrementalTransformInput.path}

The Compass path of the dataset.

* **Type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)

### *property* rid {#transforms.api.IncrementalTransformInput.rid}

The resource identifier of the dataset.

* **Type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)

### *property* start\_transaction\_rid {#transforms.api.IncrementalTransformInput.start\_transaction\_rid}

The starting transaction of the input dataset.

* **Type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)
