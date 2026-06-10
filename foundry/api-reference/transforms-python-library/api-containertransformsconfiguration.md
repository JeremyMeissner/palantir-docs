---
source_url: "https://www.palantir.com/docs/foundry/api-reference/transforms-python-library/api-containertransformsconfiguration/"
title: "Documentation | transforms.api > ContainerTransformsConfiguration"
---
# transforms.api.ContainerTransformsConfiguration

## *class* transforms.api.ContainerTransformsConfiguration(transform, \*, cpu\_cores=None, memory\_mb=None, memory\_gb=None, gpu\_type=None, container\_image=None, container\_tag=None, container\_shell\_command=None, incremental\_override=None, identifier\_override=None) {#transforms.api.ContainerTransformsConfiguration}

A callable object that describes a single step of a lightweight, single-node computation.

A [`ContainerTransform`](/docs/foundry/api-reference/transforms-python-library/api-containertransform/#transforms.api.ContainerTransform) consists of a number of parameters that subclass the [`Param`](/docs/foundry/api-reference/transforms-python-library/api-param/#transforms.api.Param) class and a compute function.

It is idiomatic to construct a [`Transform`](/docs/foundry/api-reference/transforms-python-library/api-transform/#transforms.api.Transform) object using the provided decorator: [`transform.using()`](/docs/foundry/api-reference/transforms-python-library/api-transform/#transforms.api.transform.using).

Note that the original compute function is exposed via the [`ContainerTransform`](/docs/foundry/api-reference/transforms-python-library/api-containertransform/#transforms.api.ContainerTransform)’s `__call__()` method.

:::callout{theme="neutral"}
Overload of [`ContainerTransform`](/docs/foundry/api-reference/transforms-python-library/api-containertransform/#transforms.api.ContainerTransform) for backwards compatibility.
:::

### *property* reference {#transforms.api.ContainerTransformsConfiguration.reference}

A reference to this transform, unique in the pipeline. This field is recomputed at each call to account for compute function renaming.
