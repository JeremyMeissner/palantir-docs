---
source_url: "https://www.palantir.com/docs/foundry/api-reference/transforms-python-library/api-dataset/"
title: "Documentation | transforms.api > Dataset"
---
# foundry.transforms.Dataset

## *class* foundry.transforms.Dataset(alias) {#foundry.transforms.Dataset}

A class representing the files backing a Foundry dataset view.

Prefer using the static [`Dataset.get()`](#foundry.transforms.Dataset.get) factory method instead of calling the constructor directly.

### *static method* get(alias) {#foundry.transforms.Dataset.get}

Create a new `Dataset` instance for the given alias.

* **Parameters:**
  **alias** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str)) – The alias of the dataset.
* **Returns:**
  A new `Dataset` instance.
* **Return type:**
  [`Dataset`](#foundry.transforms.Dataset)

### *property* alias {#foundry.transforms.Dataset.alias}

The alias of the dataset.

* **Type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)

### *property* schema {#foundry.transforms.Dataset.schema}

The Foundry field schema of the dataset.

* **Type:**
  `FoundryFieldSchema`

### *property* write\_table\_path {#foundry.transforms.Dataset.write\_table\_path}

The path on disk for the dataset files to be used with `write_table`.

* **Type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)

### *property* lazy\_write\_table\_path {#foundry.transforms.Dataset.lazy\_write\_table\_path}

An object store path to a bucket that will be mapped into the output transaction.

* **Type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)

### read\_table(columns=None, row\_limit=None, format='dataframe', mode='current', force\_dataset\_download=False, schema=None) {#foundry.transforms.Dataset.read\_table}

Read a tabular Foundry dataset as a pandas DataFrame, Polars DataFrame, Arrow Table, or raw file path.

* **Parameters:**
  * **columns** (*List* *\[*[*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *]* *,* *optional*) – The subset of columns to read.
  * **row\_limit** ([*int* ↗](https://docs.python.org/3/library/functions.html#int) *,* *optional*) – The maximum number of rows to read.
  * **format** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – The output type. One of `"arrow"`, `"pandas"`, `"dataframe"` (alias for pandas, default), `"polars"`, `"lazy-polars"`, or `"path"`. When set to `"path"`, a path pointing to the raw dataset files is returned.
  * **mode** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – The read mode, one of `"current"`, `"previous"`, or `"added"`. Defaults to `"current"`.
  * **force\_dataset\_download** ([*bool* ↗](https://docs.python.org/3/library/functions.html#bool) *,* *optional*) – Whether the dataset must be re-downloaded even if present in local content. Defaults to `False`.
  * **schema** (*FoundryFieldSchema* *,* *optional*) – The schema to apply if reading an empty incremental output.
* **Returns:**
  The dataset contents in the requested format.
* **Return type:**
  [`pyarrow.Table` ↗](https://arrow.apache.org/docs/python/generated/pyarrow.Table.html) | [`pandas.DataFrame` ↗](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html#pandas.DataFrame) | [`polars.DataFrame` ↗](https://docs.pola.rs/api/python/stable/reference/dataframe/index.html) | [`polars.LazyFrame` ↗](https://docs.pola.rs/api/python/stable/reference/lazyframe/index.html) | [str ↗](https://docs.python.org/3/library/stdtypes.html#str)

:::callout{theme="neutral"}
When `columns`, `row_limit`, or filters applied via the `where()` method are set, the output `format` must be one of `"arrow"`, `"dataframe"`, `"pandas"`, or `"polars"`, and `mode` must be `"current"`.
:::

### write\_table(df, column\_descriptions=None) {#foundry.transforms.Dataset.write\_table}

Upload tabular data to a Foundry dataset. This uploads the data, infers a schema, and updates column description metadata.

Accepts a pandas DataFrame, Arrow Table, Polars DataFrame, DuckDB PyRelation, or a path (string or `pathlib.Path`) pointing to a raw dataset.

* **Parameters:**
  * **df** – The data to upload. Accepts [`pandas.DataFrame` ↗](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html#pandas.DataFrame), [`pyarrow.Table` ↗](https://arrow.apache.org/docs/python/generated/pyarrow.Table.html), [`polars.DataFrame` ↗](https://docs.pola.rs/api/python/stable/reference/dataframe/index.html), DuckDB `PyRelation`, or a path matching `write_table_path`.
  * **column\_descriptions** (*Dict* *\[*[*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* [*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *]* *,* *optional*) – Map of column names to their string descriptions. This map is intersected with the columns of the DataFrame, and must include descriptions no longer than 800 characters.
* **Returns:**
  None

### put\_metadata(column\_descriptions=None) {#foundry.transforms.Dataset.put\_metadata}

Finalize a dataset after uploading raw Parquet files. This infers a Foundry schema from the uploaded Parquet and updates column description metadata on the dataset.

:::callout{theme="neutral"}
You must call this method after one or more Parquet files have been uploaded to the output dataset so that a schema can be inferred. The method will throw if it is called before a successful file upload.
:::

* **Parameters:**
  **column\_descriptions** (*Dict* *\[*[*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* [*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *]* *,* *optional*) – Map of column names to their string descriptions. This map is intersected with the columns of the dataset, and must include descriptions no longer than 800 characters.
* **Returns:**
  None

### set\_write\_mode(mode) {#foundry.transforms.Dataset.set\_write\_mode}

Set the write mode of the dataset.

* **Parameters:**
  **mode** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str)) – The write mode, one of `"replace"`, `"modify"`, or `"append"`. In modify mode, anything written is appended to the dataset and may also override existing files. In append mode, anything written is appended to the dataset and will not override existing files. In replace mode, anything written replaces the dataset.
* **Returns:**
  None

:::callout{theme="neutral"}
The write mode cannot be changed after data has been written.
:::

### files(mode='current', show\_hidden\_files=False) {#foundry.transforms.Dataset.files}

List files in a Foundry dataset.

* **Parameters:**
  * **mode** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – The read mode, one of `"current"`, `"previous"`, or `"added"`. Defaults to `"current"`.
  * **show\_hidden\_files** ([*bool* ↗](https://docs.python.org/3/library/functions.html#bool) *,* *optional*) – Whether to list hidden files. Defaults to `False`.
* **Returns:**
  The collection of files in the dataset.
* **Return type:**
  `FileCollection`

### upload\_file(path, logical\_path=None) {#foundry.transforms.Dataset.upload\_file}

Upload a local file to a Foundry dataset.

* **Parameters:**
  * **path** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str)) – The path to the local file to upload.
  * **logical\_path** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – The destination path in the Foundry dataset. If not provided, the file is uploaded to the root with the same name as the local file.
* **Returns:**
  The name of the uploaded Foundry dataset file.
* **Return type:**
  [str ↗](https://docs.python.org/3/library/stdtypes.html#str)

### upload\_directory(local\_dir\_path) {#foundry.transforms.Dataset.upload\_directory}

Upload a local directory to a Foundry dataset. All files found recursively inside the directory will be uploaded.

* **Parameters:**
  **local\_dir\_path** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str)) – The path to the local directory to upload.
* **Returns:**
  A map of local file paths to the corresponding Foundry dataset file paths.
* **Return type:**
  *Dict* *\[*[*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* [*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *]*

### where(operand\_filter) {#foundry.transforms.Dataset.where}

Apply a row filter to the dataset. Returns the dataset so that calls can be chained. Filters are applied when `read_table` is called.

* **Parameters:**
  **operand\_filter** – A filter expression built using `Column.get()`.
* **Returns:**
  The filtered dataset.
* **Return type:**
  [`Dataset`](#foundry.transforms.Dataset)

Supported operators on `Column`:

* `==`, `!=`, `>`, `>=`, `<`, `<=`
* `.isnull()`
* `.isin(values)`
* `.between(lower, upper)`

Combine filters with `&` (and), `|` (or), and `~` (not).

```python
from foundry.transforms import Dataset
from foundry.transforms import Column

ds = Dataset.get("my_dataset")
filtered = ds.where(Column.get("age") > 18)
result = filtered.read_table(format="pandas")
```

### select(\*column\_names) {#foundry.transforms.Dataset.select}

Select a subset of columns from the dataset. Returns the dataset so that calls can be chained.

* **Parameters:**
  **column\_names** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str)) – The names of the columns to select.
* **Returns:**
  The dataset with the column selection applied.
* **Return type:**
  [`Dataset`](#foundry.transforms.Dataset)

### limit(row\_limit) {#foundry.transforms.Dataset.limit}

Set the maximum number of rows to read. Returns the dataset so that calls can be chained.

* **Parameters:**
  **row\_limit** ([*int* ↗](https://docs.python.org/3/library/functions.html#int)) – The maximum number of rows.
* **Returns:**
  The dataset with the row limit applied.
* **Return type:**
  [`Dataset`](#foundry.transforms.Dataset)

### abort() {#foundry.transforms.Dataset.abort}

Abort all work on this dataset. Any data written before or after calling this method will be ignored.

* **Returns:**
  The aborted dataset.
* **Return type:**
  [`Dataset`](#foundry.transforms.Dataset)
