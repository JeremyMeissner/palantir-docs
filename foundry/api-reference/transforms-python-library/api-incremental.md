---
source_url: "https://www.palantir.com/docs/foundry/api-reference/transforms-python-library/api-incremental/"
title: "Documentation | transforms.api > incremental"
---
# transforms.api.incremental

## transforms.api.incremental(require\_incremental=False, semantic\_version=1, snapshot\_inputs=None, allow\_retention=False, strict\_append=False, v2\_semantics=False) {#transforms.api.incremental}

A decorator to convert inputs and outputs into their [`transforms.api.incremental`](#transforms.api.incremental) counterparts.

The `incremental` decorator must be used to wrap a [`Transform`](/docs/foundry/api-reference/transforms-python-library/api-transform/#transforms.api.Transform) or [`ContainerTransform`](/docs/foundry/api-reference/transforms-python-library/api-containertransform/#transforms.api.ContainerTransform):

```python
>>> @incremental()
... @transform.using(...)
... def my_compute_function(...):
...     pass
```

If using Spark:

```python
>>> @incremental()
... @transform(...)
... def my_compute_function(...):
...     pass
```

The decorator reads build history from the output datasets to determine the state of the inputs at the time of the last build. This information is used to convert the [`TransformInput`](/docs/foundry/api-reference/transforms-python-library/api-transforminput/#transforms.api.TransformInput), [`TransformOutput`](/docs/foundry/api-reference/transforms-python-library/api-transformoutput/#transforms.api.TransformOutput) and [`TransformContext`](/docs/foundry/api-reference/transforms-python-library/api-transformcontext/#transforms.api.TransformContext) objects into their incremental counterparts; `IncrementalTransformInput`, `IncrementalTransformOutput` and `IncrementalTransformContext`.

This decorator can also be used to wrap the [`transform_df()`](/docs/foundry/api-reference/transforms-python-library/api-transform-df/#transforms.api.transform_df) and [`transform_pandas()`](/docs/foundry/api-reference/transforms-python-library/api-transform-pandas/#transforms.api.transform_pandas) decorators. These decorators call `dataframe()` and `pandas()` on the inputs without any arguments, to extract the PySpark and pandas DataFrame objects. This means that the read mode used will always be `added` and the write mode will be determined by the `incremental` decorator. For reading or writing any of the non-default modes, you must use the [`transform()`](/docs/foundry/api-reference/transforms-python-library/api-transform/#transforms.api.transform) decorator.

:::callout{theme="warning"}
If your transform performs complex logic involving joins, aggregations, distinct, etc., then it is recommended that you read the [incremental documentation ↗](/docs/foundry/transforms-python/incremental-overview/) before using this decorator.
:::

:::callout{theme="neutral"}
If the added output rows in your PySpark or pandas transform are only a function of the added input rows as shown in this [append ↗](/docs/foundry/transforms-python-spark/incremental-examples/#append) example, the default modes will produce a correct incremental transform.
:::

:::callout{theme="neutral"}
If your transform takes an input dataset that has `SNAPSHOT` transactions, but does not alter the ability to run the transform incrementally (for example, reference tables), review the `snapshot_inputs` argument. This argument can help prevent the need to run a transform as a full `SNAPSHOT`.
:::

* **Parameters:**
  * **require\_incremental** ([*bool* ↗](https://docs.python.org/3/library/functions.html#bool) *,* *optional*) – If `True`, the transform will refuse to run non-incrementally unless the transform has never been run before. This is determined based on all output datasets having no committed transactions.
  * **semantic\_version** ([*int* ↗](https://docs.python.org/3/library/functions.html#int) *,* *optional*) – Defaults to 1. This number represents the semantic nature of a transform. It should be changed whenever the logic of a transform changes in a way that would invalidate the existing output. Changing this number causes a subsequent run of the transform to be run non-incrementally.
  * **snapshot\_inputs** ([*list* ↗](https://docs.python.org/3/library/stdtypes.html#list) *of* [*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – The inputs for which a `SNAPSHOT` transaction does not invalidate the current output of a transform. For example, an update to a lookup table does not mean that previously computed outputs are incorrect. A transform is run incrementally when all inputs except for these only have added or no new data. When reading snapshot inputs, the [`transforms.api.IncrementalTransformInput`](/docs/foundry/api-reference/transforms-python-library/api-incrementaltransforminput/#transforms.api.IncrementalTransformInput) will only expose the current view of the input dataset.
  * **allow\_retention** ([*bool* ↗](https://docs.python.org/3/library/functions.html#bool) *,* *optional*) – If `True`, deletes made by foundry-retention will not break incrementality.
  * **strict\_append** ([*bool* ↗](https://docs.python.org/3/library/functions.html#bool) *,* *optional*) – If `True` and the transform runs incrementally, the underlying Foundry transaction type will be an `APPEND`. If `True` and the transform is not running incrementally, require\_incremental is required to be `True` to force an incremental `APPEND` transaction. Note that the write operation may not overwrite any files, even auxiliary ones such as Parquet summary metadata or Hadoop `SUCCESS` files. Incremental writes for all Foundry formats should support this mode.
  * **v2\_semantics** ([*bool* ↗](https://docs.python.org/3/library/functions.html#bool)) – Defaults to `False`. If `True`, will use v2 incremental semantics. There should be no difference in behavior between v2 and v1 incremental semantics, and we recommend all users set this to `True`. Non-Catalog incremental inputs and outputs are only supported if using v2 semantics.
* **Raises:**
  * **TransformTypeError** – If the object wrapped is not a [`Transform`](/docs/foundry/api-reference/transforms-python-library/api-transform/#transforms.api.Transform) object.
  * **TransformKeyError** – If the snapshot input does not exist on the [`Transform`](/docs/foundry/api-reference/transforms-python-library/api-transform/#transforms.api.Transform) object.

#### History

* Added in version 1.7.0.
* Changed in version 1.35.0: Added snapshot\_inputs
* Changed in version 1.312.0: Added strict\_append
