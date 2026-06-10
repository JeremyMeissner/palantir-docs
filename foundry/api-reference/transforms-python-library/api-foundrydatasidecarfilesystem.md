---
source_url: "https://www.palantir.com/docs/foundry/api-reference/transforms-python-library/api-foundrydatasidecarfilesystem/"
title: "Documentation | transforms.api > FoundryDataSidecarFileSystem"
---
# transforms.api.FoundryDataSidecarFileSystem

## *class* transforms.api.FoundryDataSidecarFileSystem(param, read\_only=False, read\_mode='current') {#transforms.api.FoundryDataSidecarFileSystem}

A file system for reading and writing raw dataset files in lightweight, single-node transforms.

Returns [`FoundryDataSidecarFile`](/docs/foundry/api-reference/transforms-python-library/api-foundrydatasidecarfile/#transforms.api.FoundryDataSidecarFile) objects for reading and writing files in the dataset.

### ls(glob=None, regex='.\*', show\_hidden=False) {#transforms.api.FoundryDataSidecarFileSystem.ls}

Recurses through all directories and lists all files matching the given patterns, starting from the root directory of the dataset.

* **Parameters:**
  * **glob** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – A unix file-matching pattern. Also supports globstar.
  * **regex** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – A regex pattern against which to match filenames.
  * **show\_hidden** ([*bool* ↗](https://docs.python.org/3/library/functions.html#bool) *,* *optional*) – Include hidden files, those prefixed with ‘.’ or ‘\_’.
* **Yields:**
  [`FileStatus`](/docs/foundry/api-reference/transforms-python-library/api-filestatus/#transforms.api.FileStatus) – The logical path, file size, and modified timestamp.

### open(path, mode='r', \*\*kwargs) {#transforms.api.FoundryDataSidecarFileSystem.open}

Open a FoundryFS file in the given mode.

Should be used in a `with` statement, especially when writing to a file.

* **Parameters:**
  * **path** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str)) – The logical path of the file in the dataset.
  * **mode** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str)) – The file opening mode, defaults to read.
  * **\*\*kwargs** – Remaining keyword args passed to [`io.open()` ↗](https://docs.python.org/3/library/io.html#io.open).
* **Returns:**
  a Python file-like object attached to the stream.
* **Return type:**
  File
