---
source_url: "https://www.palantir.com/docs/foundry/api-reference/transforms-python-library/api-lightweight/"
title: "Documentation | transforms.api > lightweight"
---
# transforms.api.lightweight

## transforms.api.lightweight(\_maybe\_function=None, \*, cpu\_cores=2, memory\_mb=None, memory\_gb=None, gpu\_type=None, container\_image=None, container\_tag=None, container\_shell\_command=None) {#transforms.api.lightweight}

:deprecated[Deprecated since version 3.85.0:: Use transforms.api.transform.using() instead.]

Turn a transform into a lightweight transform.

In order to use this decorator, `foundry-transforms-lib-python` must be added as a dependency.

A lightweight transform is a transform that runs without Spark, on a single node. Lightweight transforms are faster and more cost-effective for small to medium-sized datasets. Lightweight transforms also provide more methods for accessing datasets; however, they only support a subset of the API of regular transforms, including pandas and the filesystem API. For more information, see the [Python transforms documentation ↗](/docs/foundry/transforms-python/overview/).

* **Parameters:**
  * **cpu\_cores** ([*float* ↗](https://docs.python.org/3/library/functions.html#float) *,* *optional*) – The number of CPU cores to request for the transform’s container. Can be a fraction.
  * **memory\_mb** ([*float* ↗](https://docs.python.org/3/library/functions.html#float) *,* *optional*) – The amount of memory to request for the container, in MB.
  * **memory\_gb** ([*float* ↗](https://docs.python.org/3/library/functions.html#float) *,* *optional*) – The amount of memory to request for the container, in GB. The default is 16 GB.
  * **gpu\_type** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – The type of GPU to allocate for the transform.
  * **container\_image** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – The image to use for the transform’s container.
  * **container\_tag** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – The image tag to use for the transform’s container.
  * **container\_shell\_command** ([*str* ↗](https://docs.python.org/3/library/stdtypes.html#str) *,* *optional*) – The shell command to execute inside the container after it has started. When left unspecified, a default command is generated resulting in executing the decorated transform. The default values is available through the decorated transform’s `default_container_entrypoint` property.

#### Notes

Either `memory_gb` or `memory_mb` can be specified, but not both.

In case any of `container_image`, `container_tag` or `container_shell_command` is set, both `container_image` and `container_tag` must be set. If `container_shell_command` is not set, a default entrypoint will be used, which will bootstrap a Python environment and execute the user code specified in the transform.

Specifying the `container_*` arguments is referred to as a bring-your-own-container (BYOC) workflow. In this case, the main guarantees are that all files from the user’s code repository will be available inside `$USER_WORKING_DIR/user_code` at runtime, and that a Python environment will be available as well.

The `container_image` must be available from an artifacts-backing repository of the code repository. For more details, refer to the [BYOC documentation ↗](/docs/foundry/transforms-python/bring-container/).

An example of a valid `container_image`’s Dockerfile is shown below:

```dockerfile
FROM ubuntu:latest

RUN apt update && apt install -y coreutils curl sed

RUN useradd --uid 5001 user
USER 5001
```

#### Examples

```python
>>> @lightweight
... @transform(
...     my_input=Input('/input'),
...     my_output=Output('/output')
... )
... def compute_func(my_input, my_output):
...     my_output.write_pandas(my_input.pandas())
```

```python
>>> @lightweight()
... @transform(
...    my_input=Input('/input'),
...    my_output=Output('/output')
... )
... def compute_func(my_input, my_output):
...     for file in my_input.filesystem().ls():
...         with my_input.filesystem().open(file.path) as f1:
...             with my_output.filesystem().open(file.path, "w") as f2:
...                 f2.write(f1.read())
```

```python
>>> @lightweight(cpu_cores=8, memory_gb=3.5, gpu_type='NVIDIA_T4')
... @transform_pandas(
...     Output('/output'),
...     my_input=Input('/input')
... )
... def compute_func(my_input):
...     return my_input
```

```python
>>> @lightweight(container_image='my-image', container_tag='0.0.1')
... @transform(my_output=Output('ri...my_output'))
... def run_data_generator_executable(my_output):
...     os.system('$USER_WORKING_DIR/data_generator')
...     my_output.write_table(pd.read_csv('data.csv'))
```
