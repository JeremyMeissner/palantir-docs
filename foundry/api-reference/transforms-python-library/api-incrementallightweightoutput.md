---
source_url: "https://www.palantir.com/docs/foundry/api-reference/transforms-python-library/api-incrementallightweightoutput/"
title: "Documentation | transforms.api > IncrementalLightweightOutput"
---
# transforms.api.IncrementalLightweightOutput

## *class* transforms.api.IncrementalLightweightOutput(alias, rid, branch=None) {#transforms.api.IncrementalLightweightOutput}

The output object passed into user code at runtime for incremental [`ContainerTransform`](/docs/foundry/api-reference/transforms-python-library/api-containertransform/#transforms.api.ContainerTransform) objects.

The aim is to mimic a subset of the [`transforms.api.IncrementalTransformOutput`](/docs/foundry/api-reference/transforms-python-library/api-incrementaltransformoutput/#transforms.api.IncrementalTransformOutput) API, while providing access to the underlying `foundry.transforms.Dataset`.

### *property* alias {#transforms.api.IncrementalLightweightOutput.alias}

The alias of the dataset this parameter is associated with.

### arrow(mode='current', schema=None) {#transforms.api.IncrementalLightweightOutput.arrow}

A PyArrow table containing the view of the dataset.

* **Parameters:**
  * **mode** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str)) – The read mode, one of `current`, `previous`, or `added`.  Defaults to `current`.
  * **schema** – The schema to read empty datasets with. Only used if the dataset is empty.

### *property* branch {#transforms.api.IncrementalLightweightOutput.branch}

The branch of the dataset this parameter is associated with.

### dataframe(mode='current', schema=None) {#transforms.api.IncrementalLightweightOutput.dataframe}

A pandas DataFrame containing the view of the dataset.

* **Parameters:**
  * **mode** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str)) – The read mode, one of `current`, `previous`, or `added`.  Defaults to `current`.
  * **schema** – The schema to read empty datasets with. Only used if the dataset is empty.

### filesystem() {#transforms.api.IncrementalLightweightOutput.filesystem}

Access the filesystem.

Construct a [`FoundryDataSidecarFileSystem`](/docs/foundry/api-reference/transforms-python-library/api-foundrydatasidecarfilesystem/#transforms.api.FoundryDataSidecarFileSystem) object for accessing the dataset’s files directly.

### pandas(mode='current', schema=None) {#transforms.api.IncrementalLightweightOutput.pandas}

A pandas DataFrame containing the view of the dataset.

* **Parameters:**
  * **mode** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str)) – The read mode, one of `current`, `previous`, or `added`.  Defaults to `current`.
  * **schema** – The schema to read empty datasets with. Only used if the dataset is empty.

### path(mode='current') {#transforms.api.IncrementalLightweightOutput.path}

Download the dataset’s underlying files and return a path to them.

* **Parameters:**
  **mode** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str)) – The read mode, one of `current`, `previous`, or `added`.  Defaults to `current`. This argument is only applicable when `@incremental` is added and `v2_semantics` is `True`.

### *property* path\_for\_object\_store\_write\_table {#transforms.api.IncrementalLightweightOutput.path\_for\_object\_store\_write\_table}

Returns a virtual object store path to a bucket that will be mapped into the output transaction. This does not point directly at a bucket in cloud storage, but rather at a local S3 proxy to allow query engines to perform async, optimized IO against the data.

### *property* path\_for\_write\_table {#transforms.api.IncrementalLightweightOutput.path\_for\_write\_table}

Return the path for the dataset’s files to be used with `write_table`.

### polars(lazy=False, mode='current', schema=None) {#transforms.api.IncrementalLightweightOutput.polars}

A Polars DataFrame or LazyFrame containing the view of the dataset.

* **Parameters:**
  * **lazy** ([*bool* ↗](https://docs.python.org/3/library/functions.html#bool) *,* *optional*) – Whether to return a LazyFrame or DataFrame. Defaults to `False`.
  * **mode** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str)) – The read mode, one of `current`, `previous`, or `added`.  Defaults to `current`.
  * **schema** – The schema to read empty datasets with. Only used if the dataset is empty.

### put\_metadata(column\_descriptions=None) {#transforms.api.IncrementalLightweightOutput.put\_metadata}

Method to finalize a dataset after uploading raw Parquet files. This will infer and upload a Foundry Schema from the uploaded Parquet (overwriting it if it already exists), and update column description metadata on the dataset.

:::callout{theme="neutral"}
This method must be called after one or more Parquet files have been uploaded to the output dataset so that a schema can be inferred. This method will throw an error if it is called before a successful file upload.
:::

* **Parameters:**
  **column\_descriptions** (*Dict* *\[*[*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* [*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *]* *,* *optional*) – Map of column names to their string descriptions. This map is intersected with the columns of the DataFrame, and must include descriptions no longer than 800 characters.

### read\_unstaged\_dataset\_as\_polars\_lazy() {#transforms.api.IncrementalLightweightOutput.read\_unstaged\_dataset\_as\_polars\_lazy}

Read the local version of the dataset as a Polars LazyFrame.

This method is used when computing expectations on the dataset. It must happen before the dataset is committed, since expectations can abort the build if failed.

### *property* rid {#transforms.api.IncrementalLightweightOutput.rid}

The unique resource identifier of the dataset this parameter is associated with.

### set\_mode(mode) {#transforms.api.IncrementalLightweightOutput.set\_mode}

Set the mode for the output dataset.

* **Parameters:**
  **mode** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str)) –

  The write mode, one of replace, modify, or append. In modify mode, anything written is appended to the dataset, this may also override existing files. In append mode, anything written is appended to the dataset, and will not override existing files. In replace mode, anything written replaces the dataset.

  The write mode cannot be changed after data is written.

### *property* transaction\_rid {#transforms.api.IncrementalLightweightOutput.transaction\_rid}

The transaction on the output dataset.

* **Type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)

### write\_dataframe(df, column\_description=None, column\_descriptions=None) {#transforms.api.IncrementalLightweightOutput.write\_dataframe}

Write a DataFrame of any supported type to the dataset.

For compatibility reasons, both `column_description` and `column_descriptions` are accepted. However, only one of them can be provided at the same time.

* **Parameters:**
  * **df** – `pd.DataFrame`, `pa.Table`, `pl.DataFrame`, `pl.LazyFrame`, `duckdb.DuckDBPyRelation` or `pathlib.Path` with the data to upload.
  * **column\_description** (*Dict* *\[*[*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* [*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *]* *,* *optional*) – Deprecated, use `column_descriptions` instead.
  * **column\_descriptions** (*Dict* *\[*[*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* [*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *]* *,* *optional*) – Map of column names to their string descriptions. This map is intersected with the columns of the DataFrame, and must include descriptions no longer than 800 characters.
* **Returns:**
  None

### write\_pandas(df, column\_description=None, column\_descriptions=None) {#transforms.api.IncrementalLightweightOutput.write\_pandas}

Write the given [`pandas.DataFrame` ↗](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html#pandas.DataFrame) to the dataset.

For compatibility reasons, both `column_description` and `column_descriptions` are accepted. However, only one of them can be provided at the same time.

### write\_table(df, column\_description=None, column\_descriptions=None) {#transforms.api.IncrementalLightweightOutput.write\_table}

Write a pandas DataFrame, Arrow Table, Polars DataFrame or LazyFrame, to a Foundry dataset.

This has three operations: uploading the `df` itself to the dataset, inferring a schema and putting it to the dataset (overwriting it if it already exists), and updating column description metadata. To update only the metadata without uploading data, use [`put_metadata()`](#transforms.api.IncrementalLightweightOutput.put_metadata) instead.

:::callout{theme="neutral"}
For compatibility reasons, both `column_description` and `column_descriptions` are accepted. However, only one of them can be provided at the same time.
:::

* **Parameters:**
  * **df** – `pd.DataFrame`, `pa.Table`, `pl.DataFrame`, `pl.LazyFrame`, `duckdb.DuckDBPyRelation` or `pathlib.Path` with the data to upload, or `None` to just infer a schema from data previously written in the transaction.
  * **column\_description** (*Dict* *\[*[*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* [*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *]* *,* *optional*) – Deprecated, use `column_descriptions` instead.
  * **column\_descriptions** (*Dict* *\[*[*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* [*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *]* *,* *optional*) – Map of column names to their string descriptions. This map is intersected with the columns of the DataFrame, and must include descriptions no longer than 800 characters.
* **Returns:**
  None
