---
source_url: "https://www.palantir.com/docs/foundry/api-reference/transforms-python-library/api-computebackend/"
title: "Documentation | transforms.api > ComputeBackend"
---
# transforms.api.ComputeBackend

## *class* transforms.api.ComputeBackend(\*values) {#transforms.api.ComputeBackend}

Enum class for representing the different compute backends for use in [`configure()`](/docs/foundry/api-reference/transforms-python-library/api-configure/#transforms.api.configure).

The following are available backends:

* `SPARK`
* `VELOX`

VELOX will run Spark with native acceleration. See [Native Acceleration ↗](/docs/foundry/optimizing-pipelines/native-acceleration/) for more information.

#### Example

```python
>>> @configure(backend=ComputeBackend.SPARK)
... @transform(...)
... def my_compute_function(...):
...     pass
```
