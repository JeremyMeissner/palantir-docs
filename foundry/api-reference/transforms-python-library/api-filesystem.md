---
source_url: "https://www.palantir.com/docs/foundry/api-reference/transforms-python-library/api-filesystem/"
title: "Documentation | transforms.api > FileSystem"
---
# transforms.api.FileSystem

## *class* transforms.api.FileSystem(foundry\_fs, read\_only=False) {#transforms.api.FileSystem}

A filesystem object for reading and writing raw dataset files in Spark transforms.

:::callout{theme="neutral"}
For lightweight, single-node transforms, see [`transforms.api.FoundryDataSidecarFileSystem`](/docs/foundry/api-reference/transforms-python-library/api-foundrydatasidecarfilesystem/#transforms.api.FoundryDataSidecarFileSystem).
:::

### files(glob=None, regex='.\*', show\_hidden=False, packing\_heuristic=None) {#transforms.api.FileSystem.files}

Create a [`DataFrame` ↗](https://spark.apache.org/docs/latest/api/python/reference/pyspark.sql/api/pyspark.sql.DataFrame.html#pyspark.sql.DataFrame) containing the paths accessible within this dataset.

The [`DataFrame` ↗](https://spark.apache.org/docs/latest/api/python/reference/pyspark.sql/api/pyspark.sql.DataFrame.html#pyspark.sql.DataFrame) is partitioned by file size where each partition contains file paths whose combined size is at most `spark.files.maxPartitionBytes` bytes, or a single file if that file is larger than `spark.files.maxPartitionBytes`. The size of a file is calculated as its on-disk file size plus the `spark.files.openCostInBytes`.

* **Parameters:**
  * **glob** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – A unix file-matching pattern. Also supports globstar.
  * **regex** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – A regex pattern against which to match filenames.
  * **show\_hidden** ([*bool* ↗](https://docs.python.org/3/library/functions.html#bool) *,* *optional*) – Include hidden files, those prefixed with ‘.’ or ‘\_’.
  * **packing\_heuristic** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – Specify a heuristic to use for bin-packing files into Spark partitions. Possible choices are `ffd` (first fit decreasing) or `wfd` (worst fit decreasing). While `wfd` tends to produce a less even distribution, it is much faster, so `wfd` is recommended for datasets containing a very large number of files. If a heuristic is not specified, one will be selected automatically.
* **Returns:**
  A DataFrame of (path, size, modified)
* **Return type:**
  [pyspark.sql.DataFrame ↗](https://spark.apache.org/docs/latest/api/python/reference/pyspark.sql/api/pyspark.sql.DataFrame.html#pyspark.sql.DataFrame)

### *property* hadoop\_path {#transforms.api.FileSystem.hadoop\_path}

Fetches the Hadoop path of the dataset, which can be used for code that requires direct Hadoop IO.

* **Returns:**
  The Hadoop path of the dataset backing this FileSystem or `None`
* **Return type:**
  string

### ls(glob=None, regex='.\*', show\_hidden=False) {#transforms.api.FileSystem.ls}

Recurses through all directories and lists all files matching the given patterns, starting from the root directory of the dataset.

* **Parameters:**
  * **glob** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – A unix file-matching pattern. Also supports globstar.
  * **regex** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – A regex pattern against which to match filenames.
  * **show\_hidden** ([*bool* ↗](https://docs.python.org/3/library/functions.html#bool) *,* *optional*) – Include hidden files, those prefixed with ‘.’ or ‘\_’.
* **Yields:**
  [`FileStatus`](/docs/foundry/api-reference/transforms-python-library/api-filestatus/#transforms.api.FileStatus) – The logical path, file size (bytes), and modified timestamp (ms since January 1, 1970 UTC)

### open(path, mode='r', \*\*kwargs) {#transforms.api.FileSystem.open}

Open a FoundryFS file in the given mode.

* **Parameters:**
  * **path** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str)) – The logical path of the file in the dataset.
  * **mode** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str)) – File opening mode, defaults to read.
  * **\*\*kwargs** – Remaining keyword args passed to [`io.open()` ↗](https://docs.python.org/3/library/io.html#io.open).
* **Returns:**
  a Python file-like object attached to the stream.
* **Return type:**
  File
