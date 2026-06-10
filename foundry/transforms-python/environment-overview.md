---
source_url: "https://www.palantir.com/docs/foundry/transforms-python/environment-overview/"
parquet_url: "/foundry/transforms-python/environment-overview/"
title: "Python environment"
fetched_at: "2026-05-12T19:34:36.004Z"
---
Python environment. The Python environment used for a transform is resolved during Checks using the Hawk package manager based on the specified list of packages in the conda_recipe/meta.yaml file. Using the package tab, you can discover available packages and automatically add these to your meta.yml for environment resolution. This resolved environment is published internally to Artifacts ready for use during the build. When the transform is built, it fetches the environment file and installs the required packages specified in the environment file. If this fails for some reason, the transform will fall back to resolving the environment again during the build using Hawk. Useful resources. See Introduction to Environment Creation for an introduction to using Conda, Mamba, and Hawk to create environments. For general troubleshooting of common environment problems, see Environment Troubleshooting Guide.
