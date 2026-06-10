---
source_url: "https://www.palantir.com/docs/foundry/api-reference/transforms-python-library/api-lightweightcontext/"
title: "Documentation | transforms.api > LightweightContext"
---
# transforms.api.LightweightContext

## *class* transforms.api.LightweightContext {#transforms.api.LightweightContext}

A context object that can optionally be injected into the compute function of a lightweight transform.

Can be accessed by adding a `ctx` argument to the compute function as shown below:

```python
>>> @transform.using(...)
... def compute(ctx, ...):
...     ...
```

Equivalent to [`transforms.api.TransformContext`](/docs/foundry/api-reference/transforms-python-library/api-transformcontext/#transforms.api.TransformContext) for single node compute.

### abort\_job() {#transforms.api.LightweightContext.abort\_job}

Aborts the job and ends execution. This will abort all output transactions.

### *property* auth\_header {#transforms.api.LightweightContext.auth\_header}

The auth header used to run the transform.

### *property* is\_incremental {#transforms.api.LightweightContext.is\_incremental}

Whether the transform is running incrementally.
