---
source_url: "https://www.palantir.com/docs/foundry/api-reference/transforms-python-library/api-paramcontext/"
title: "Documentation | transforms.api > ParamContext"
---
# transforms.api.ParamContext

## *class* transforms.api.ParamContext(foundry\_connector, input\_specs, output\_specs, branch, param\_overrides, job\_rid=None) {#transforms.api.ParamContext}

A context object injected in the `instance` method of a parameter.

* **Parameters:**
  * **foundry\_connector** (*FoundryConnector*) – The `transforms.foundry.connectors.FoundryConnector` object.
  * **input\_specs** ([*dict* ↗](https://docs.python.org/3/library/stdtypes.html#dict)) – A map from resource identifier (RID) to the input spec entry from JobSpec.
  * **output\_specs** ([*dict* ↗](https://docs.python.org/3/library/stdtypes.html#dict)) – A map from RID to the output spec entry from JobSpec.
  * **branch** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str)) – The branch name this build is running on.
  * **param\_overrides** – A map of from param\_name to override
  * **job\_rid** (*Optional* *\[*[*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *]*) – The job RID.

#### History

* Added in version 1.53.0.
