---
source_url: "https://www.palantir.com/docs/foundry/api-reference/transforms-python-library/api-param/"
title: "Documentation | transforms.api > Param"
---
# transforms.api.Param

## *class* transforms.api.Param(description=None) {#transforms.api.Param}

Base class for any parameter taken by the transform compute function.

* **Parameters:**
  **description** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – The parameter description to be added in the JSON schema.

### *static* instance(context, json\_value) {#transforms.api.Param.instance}

Creates a parameter instance using the raw JSON value from JobSpec parameters and specific context.

The return value is injected in the transform compute function.

* **Parameters:**
  * **context** ([*ParamContext*](/docs/foundry/api-reference/transforms-python-library/api-paramcontext/#transforms.api.ParamContext)) – A context object with properties that might be required for creating an instance.
  * **json\_value** (*any*) – Any raw value deserialized from JobSpec parameters.

#### History

* Added in version 1.53.0.

### *property* json\_value {#transforms.api.Param.json\_value}

Returns the JSON value for this parameter to put in JobSpec.

If the return value is `None`, the parameter is considered unbound. If any transform’s parameter is unbound, the transform is considered to be unbound. For unbound transforms, the JobSpec is not published.

### *property* schema {#transforms.api.Param.schema}

Returns JSON schema for parameters of this type. Must return a valid JSON schema.
