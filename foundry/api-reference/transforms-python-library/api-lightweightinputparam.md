---
source_url: "https://www.palantir.com/docs/foundry/api-reference/transforms-python-library/api-lightweightinputparam/"
title: "Documentation | transforms.api > LightweightInputParam"
---
# transforms.api.LightweightInputParam

## *class* transforms.api.LightweightInputParam {#transforms.api.LightweightInputParam}

Base type for input parameters compatible with lightweight, single node transforms. Inheritors must also inherit [`FoundryInputParam`](/docs/foundry/api-reference/transforms-python-library/api-foundryinputparam/#transforms.api.FoundryInputParam).

See [`transforms.api.Input`](/docs/foundry/api-reference/transforms-python-library/api-input/#transforms.api.Input) for an example of concrete usage.

### *abstractmethod static* lightweight\_instance(context, json\_value) {#transforms.api.LightweightInputParam.lightweight\_instance}

Instantiate an input type from the resolved JSON value.
