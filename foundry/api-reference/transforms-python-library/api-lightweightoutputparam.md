---
source_url: "https://www.palantir.com/docs/foundry/api-reference/transforms-python-library/api-lightweightoutputparam/"
title: "Documentation | transforms.api > LightweightOutputParam"
---
# transforms.api.LightweightOutputParam

## *class* transforms.api.LightweightOutputParam {#transforms.api.LightweightOutputParam}

Base type for output parameters compatible with lightweight, single node transforms. Inheritors must also inherit [`FoundryOutputParam`](/docs/foundry/api-reference/transforms-python-library/api-foundryoutputparam/#transforms.api.FoundryOutputParam).

See [`transforms.api.Output`](/docs/foundry/api-reference/transforms-python-library/api-output/#transforms.api.Output) for an example of concrete usage.

### *abstractmethod static* lightweight\_instance(context, json\_value) {#transforms.api.LightweightOutputParam.lightweight\_instance}

Instantiate an output type from the resolved JSON value.
