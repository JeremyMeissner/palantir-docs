---
source_url: "https://www.palantir.com/docs/foundry/api-reference/transforms-python-library/api-incrementaltabletransforminput/"
title: "Documentation | transforms.api > IncrementalTableTransformInput"
---
# transforms.api.IncrementalTableTransformInput

## *class* transforms.api.IncrementalTableTransformInput(table\_tinput, from\_version) {#transforms.api.IncrementalTableTransformInput}

[`TableTransformInput`](/docs/foundry/api-reference/transforms-python-library/api-tabletransforminput/#transforms.api.TableTransformInput) with added functionality for incremental computation.

### *property* batch\_incremental\_configuration {#transforms.api.IncrementalTableTransformInput.batch\_incremental\_configuration}

The configuration for an incremental input that will be read in batches.

* **Type:**
  `BatchIncrementalConfiguration`

### *property* branch {#transforms.api.IncrementalTableTransformInput.branch}

The branch of the dataset.

* **Type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)

### *property* catalog {#transforms.api.IncrementalTableTransformInput.catalog}

Returns the name of the table’s Spark catalog, intended for use in Spark procedures, if supported by the underlying table type.

* **Returns:**
  The name of the table’s catalog.
* **Return type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)
* **Raises:**
  [**ValueError** ↗](https://docs.python.org/3/library/exceptions.html#ValueError) – If the underlying table type does not expose a Spark catalog.

### changelog(identifier\_columns=None) {#transforms.api.IncrementalTableTransformInput.changelog}

Creates a changelog view for the given table from the last processed snapshot ID.

Note: Only supported for Iceberg tables.

If the identifier columns are provided, this creates a identifier-based changelog. This changelog type gives you the last changes performed on rows uniquely identified by the given identifier columns. This is more performant and allows greater flexibility while performing row edits.

Without identifier columns, it creates a net-changes changelog. This changelog type gives you the coalesced changes performed on the rows by cancelling out `DELETES` and `INSERTS` over the snapshot range. This leads to a high amount of data shuffling and is slower than an identifier-based changelog.

If this changelog is intended to be used in updating an output table, the identifier columns used when creating this changelog should match the identifier columns used to update the output table.

See the Iceberg [create\_changelog\_view ↗](https://iceberg.apache.org/docs/latest/spark-procedures/#create_changelog_view) documentation for more information.

* **Parameters:**
  **identifier\_columns** (*List* *\[*[*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *]* *,* *optional*) – The list of columns that uniquely identify each row, if present.
* **Returns:**
  Temporary changelog view with original table schema along with `_change_type`, `_change_ordinal` and `_commit_snapshot_id` columns. For an identifier-based changelog, `_change_type` can either be `INSERT`, `DELETE`, `UPDATE_AFTER` or `UPDATE_BEFORE`. For a net-changes changelog, `_change_type` can either be `INSERT` or `DELETE`.
* **Return type:**
  [`DataFrame` ↗](https://spark.apache.org/docs/latest/api/python/reference/pyspark.sql/api/pyspark.sql.DataFrame.html#pyspark.sql.DataFrame)

### *property* column\_descriptions {#transforms.api.IncrementalTableTransformInput.column\_descriptions}

The column descriptions of the dataset.

* **Type:**
  `Dict[str, str]`

### *property* column\_typeclasses {#transforms.api.IncrementalTableTransformInput.column\_typeclasses}

The column typeclasses of the dataset.

* **Type:**
  `Dict[str, str]`

### dataframe(mode='added', options=None) {#transforms.api.IncrementalTableTransformInput.dataframe}

Return a [`pyspark.sql.DataFrame` ↗](https://spark.apache.org/docs/latest/api/python/reference/pyspark.sql/api/pyspark.sql.DataFrame.html#pyspark.sql.DataFrame) for the given read mode.

`changelog` read mode for Iceberg tables returns the changelog view for the given table from the last processed snapshot ID. Unlike the [`changelog()`](#transforms.api.IncrementalTableTransformInput.changelog) method, this always creates a net-changes changelog, which is not very performant but supports tables without identifier columns (a list of columns that uniquely identify each row). Note that this read mode is deprecated. Use [`changelog()`](#transforms.api.IncrementalTableTransformInput.changelog) instead.

* **Parameters:**
  * **mode** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – The read mode, one of current, previous, added, modified, removed, or changelog. Defaults to added.
  * **options** ([*dict* ↗](https://docs.python.org/3/library/stdtypes.html#dict) *,* *option*) – Additional Spark read options to pass when reading the table.
* **Returns:**
  The DataFrame for the table.
* **Return type:**
  [`DataFrame` ↗](https://spark.apache.org/docs/latest/api/python/reference/pyspark.sql/api/pyspark.sql.DataFrame.html#pyspark.sql.DataFrame)

### *property* end\_transaction\_rid {#transforms.api.IncrementalTableTransformInput.end\_transaction\_rid}

The ending transaction of the input dataset.

* **Type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)

### filesystem(mode='added') {#transforms.api.IncrementalTableTransformInput.filesystem}

Construct a FileSystem object for reading from FoundryFS for the given read mode.

Only current, previous and added modes are supported.

* **Parameters:**
  **mode** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – The read mode, one of current, previous, added, modified, or removed. Defaults to added.
* **Returns:**
  A filesystem object for the given view.
* **Return type:**
  [`FileSystem`](/docs/foundry/api-reference/transforms-python-library/api-filesystem/#transforms.api.FileSystem)

### *property* identifier {#transforms.api.IncrementalTableTransformInput.identifier}

Returns the full-qualified, catalog-prefixed, Spark V2 identifier of the table, if supported by the underlying table type.

* **Returns:**
  The full-qualified identifier of the table.
* **Return type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)
* **Raises:**
  [**ValueError** ↗](https://docs.python.org/3/library/exceptions.html#ValueError) – If the underlying table type does not expose a Spark V2 identifier.

### pandas() {#transforms.api.IncrementalTableTransformInput.pandas}

[`pandas.DataFrame` ↗](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html#pandas.DataFrame): A Pandas dataframe containing the full view of the dataset.

### *property* path {#transforms.api.IncrementalTableTransformInput.path}

The Compass path of the dataset.

* **Type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)

### *property* rid {#transforms.api.IncrementalTableTransformInput.rid}

The resource identifier of the dataset.

* **Type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)

### *property* start\_transaction\_rid {#transforms.api.IncrementalTableTransformInput.start\_transaction\_rid}

The starting transaction of the input dataset.

* **Type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)
