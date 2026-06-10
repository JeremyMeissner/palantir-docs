---
source_url: "https://www.palantir.com/docs/foundry/api-reference/transforms-python-library/api-incrementaltransformoutput/"
title: "Documentation | transforms.api > IncrementalTransformOutput"
---
# transforms.api.IncrementalTransformOutput

## *class* transforms.api.IncrementalTransformOutput(toutput, prev\_txrid=None, mode='replace') {#transforms.api.IncrementalTransformOutput}

[`TransformOutput`](/docs/foundry/api-reference/transforms-python-library/api-transformoutput/#transforms.api.TransformOutput) with added functionality for incremental computation.

### abort() {#transforms.api.IncrementalTransformOutput.abort}

Aborts all work on this output. Any work done on writers from this output before or after calling this method will be ignored.

#### History

* Added in version 1.7.0.

### *property* batch\_incremental\_configuration {#transforms.api.IncrementalTransformOutput.batch\_incremental\_configuration}

The configuration for an incremental input that will be read in batches.

* **Type:**
  `BatchIncrementalConfiguration`

### *property* branch {#transforms.api.IncrementalTransformOutput.branch}

The branch of the dataset.

* **Type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)

### *property* column\_descriptions {#transforms.api.IncrementalTransformOutput.column\_descriptions}

The column descriptions of the dataset.

* **Type:**
  `Dict[str, str]`

### *property* column\_typeclasses {#transforms.api.IncrementalTransformOutput.column\_typeclasses}

The column typeclasses of the dataset.

* **Type:**
  `Dict[str, str]`

### dataframe(mode='current', schema=None) {#transforms.api.IncrementalTransformOutput.dataframe}

Return a [`pyspark.sql.DataFrame` ↗](https://spark.apache.org/docs/latest/api/python/reference/pyspark.sql/api/pyspark.sql.DataFrame.html#pyspark.sql.DataFrame) for the given read mode.

* **Parameters:**
  * **mode** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – The read mode, one of added, current, or previous. Defaults to current.
  * **schema** (*pyspark.types.StructType* *,* *optional*) – A PySpark schema to use when constructing an empty DataFrame. Required when using the `previous` read mode if there is no previous transaction.
* **Returns:**
  The DataFrame for the dataset.
* **Return type:**
  [`DataFrame` ↗](https://spark.apache.org/docs/latest/api/python/reference/pyspark.sql/api/pyspark.sql.DataFrame.html#pyspark.sql.DataFrame)
* **Raises:**
  **ValueError** – If no schema is passed when using `previous` mode, and there is no previous transaction.

### *property* end\_transaction\_rid {#transforms.api.IncrementalTransformOutput.end\_transaction\_rid}

The ending transaction of the input dataset.

* **Type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)

### filesystem(mode='current') {#transforms.api.IncrementalTransformOutput.filesystem}

Construct a FileSystem object for writing to FoundryFS.

* **Parameters:**
  **mode** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – The read mode, one of added, current, or previous. Defaults to current. Only the current filesystem is writable.

### *classmethod* from\_transform\_output(instance, delegate) {#transforms.api.IncrementalTransformOutput.from\_transform\_output}

Sets fields in a TransformOutput instance to the values from the delegate TransformOutput.

### pandas(mode='current', schema=None) {#transforms.api.IncrementalTransformOutput.pandas}

[`pandas.DataFrame` ↗](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html#pandas.DataFrame): A pandas dataframe for the given read mode.

### *property* path {#transforms.api.IncrementalTransformOutput.path}

The Compass path of the dataset.

* **Type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)

### *property* rid {#transforms.api.IncrementalTransformOutput.rid}

The resource identifier of the dataset.

* **Type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)

### set\_mode(mode) {#transforms.api.IncrementalTransformOutput.set\_mode}

Change the write mode of the dataset.

* **Parameters:**
  **mode** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str)) – The write mode, one of replace, modify, or append. In modify mode, anything written is appended to the dataset. In replace mode, anything written replaces the dataset. In append mode, anything written is appended to the dataset and will not override existing files.

:::callout{theme="neutral"}
The write mode cannot be changed after data has been written.
:::

#### History

* Added in version 1.61.0.

### *property* start\_transaction\_rid {#transforms.api.IncrementalTransformOutput.start\_transaction\_rid}

The starting transaction of the input dataset.

* **Type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)

### write\_dataframe(df, partition\_cols=None, bucket\_cols=None, bucket\_count=None, sort\_by=None, output\_format=None, options=None, column\_descriptions=None, column\_typeclasses=None) {#transforms.api.IncrementalTransformOutput.write\_dataframe}

Write the given [`DataFrame` ↗](https://spark.apache.org/docs/latest/api/python/reference/pyspark.sql/api/pyspark.sql.DataFrame.html#pyspark.sql.DataFrame) to the dataset.

* **Parameters:**
  * **df** ([*pyspark.sql.DataFrame* ↗](https://spark.apache.org/docs/latest/api/python/reference/pyspark.sql/api/pyspark.sql.DataFrame.html#pyspark.sql.DataFrame)) – The PySpark DataFrame to write.
  * **partition\_cols** (*List* *\[*[*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *]* *,* *optional*) – Column partitioning to use when writing data.
  * **bucket\_cols** (*List* *\[*[*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *]* *,* *optional*) – The columns by which to bucket the data. Must be specified if `bucket_count` is given.
  * **bucket\_count** ([*int* ↗](https://docs.python.org/3/library/functions.html#int) *,* *optional*) – The number of buckets. Must be specified if `bucket_cols` is given.
  * **sort\_by** (*List* *\[*[*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *]* *,* *optional*) – The columns by which to sort the bucketed data.
  * **output\_format** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – The output file format, defaults to `parquet`.
  * **options** ([*dict* ↗](https://docs.python.org/3/library/stdtypes.html#dict) *,* *optional*) – Extra options to pass through to `org.apache.spark.sql.DataFrameWriter#option(String, String)`.
  * **column\_descriptions** (*Dict* *\[*[*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* [*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *]* *,* *optional*) – Map of column names to their string descriptions. This map is intersected with the columns of the DataFrame, and must include descriptions no longer than 800 characters.
  * **column\_typeclasses** (*Dict* *\[*[*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *List* \*\[\**Dict* *\[*[*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* [*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *]* *]* *]* *,* *optional*) – Map of column names to their column typeclasses. Each typeclass in the List is a `Dict[str, str]`, where only two keys are valid; `name` and `kind`. Each maps to the corresponding string the user wants, up to a maximum of 100 characters. An example `column_typeclasses` value would be `{"my_column": [{"name": "my_typeclass_name", "kind": "my_typeclass_kind"}]}`.

### write\_pandas(pandas\_df) {#transforms.api.IncrementalTransformOutput.write\_pandas}

Write the given [`pandas.DataFrame` ↗](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html#pandas.DataFrame) to the dataset.

* **Parameters:**
  **pandas\_df** ([*pandas.DataFrame* ↗](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html#pandas.DataFrame)) – The DataFrame to write.
