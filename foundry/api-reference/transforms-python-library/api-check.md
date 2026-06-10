---
source_url: "https://www.palantir.com/docs/foundry/api-reference/transforms-python-library/api-check/"
title: "Documentation | transforms.api > Check"
---
# transforms.api.Check

## *class* transforms.api.Check(expectation, name, on\_error='FAIL', description=None) {#transforms.api.Check}

Wraps up an expectation such that it can be registered with Data Health.

* **Parameters:**
  * **expectation** (`transforms.expectations.Expectation`) – The expectation to evaluate.
  * **name** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str)) – The name of the check, used as a stable identifier over time.
  * **on\_error** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – What action to take if the expectation is not met. Currently ‘WARN’, ‘FAIL’.
  * **description** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – The description of the check.
