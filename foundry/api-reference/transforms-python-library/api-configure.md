---
source_url: "https://www.palantir.com/docs/foundry/api-reference/transforms-python-library/api-configure/"
title: "Documentation | transforms.api > configure"
---
# transforms.api.configure

## transforms.api.configure(profile=None, allowed\_run\_duration=None, run\_as\_user=False, backend=ComputeBackend.SPARK, checkpoint\_outputs=None) {#transforms.api.configure}

A decorator that modifies the configuration of a Spark transform.

The `configure` decorator must be used to wrap a [`Transform`](/docs/foundry/api-reference/transforms-python-library/api-transform/#transforms.api.Transform):

```python
>>> @configure(profile=['high-memory'])
... @transform(...)
... def my_compute_function(...):
...     pass
```

* **Parameters:**
  * **profile** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *or* *List* *\[*[*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *]* *,* *optional*) – The transforms profile(s) to use.
  * **allowed\_run\_duration** (*timedelta* *,* *optional*) – The allowed duration for a job to complete, after which infrastructure will fail and maybe retry a job. Use carefully. When configuring allowed duration, consider variables such as changes in data scale or shape. Duration is minute precision only. IMPORTANT: Do not use for incremental transforms, as duration can change significantly when running a snapshot.
  * **run\_as\_user** (*boolean* *,* *optional*) –

    Determines whether a transforms runs with user permissions. When enabled, a job can behave differently depending on the permissions of the user running the job.

    :deprecated[Deprecated since version 3.85.0.]
  * **backend** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *or* [*ComputeBackend*](/docs/foundry/api-reference/transforms-python-library/api-computebackend/#transforms.api.ComputeBackend) *,* *optional*) – The compute backend to use for this transform. Defaults to Spark. Velox can be selected to natively accelerate the transform.
  * **checkpoint\_outputs** – The outputs that can be used for storing checkpoints. If not set, defaults to all outputs. This is particularly useful for incremental transforms where writing checkpoints to an incremental dataset may cause the build to fail.
* **Raises:**
  **TypeError** – If the wrapped object is not a [`Transform`](/docs/foundry/api-reference/transforms-python-library/api-transform/#transforms.api.Transform) object.

:::callout{theme="warning"}
The `configure` decorator can only be used on a [`Transform`](/docs/foundry/api-reference/transforms-python-library/api-transform/#transforms.api.Transform) object. This means it only applies to Spark transforms.

For more information about defining custom transforms profiles, refer to the [section on defining profiles in the Spark transforms documentation ↗](/docs/foundry/optimizing-pipelines/apply-spark-profiles/).
:::
