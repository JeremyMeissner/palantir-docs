---
source_url: "https://www.palantir.com/docs/foundry/integrate-models/container-overview/"
parquet_url: "/foundry/integrate-models/container-overview/"
title: "Container models"
fetched_at: "2026-05-12T19:34:36.853Z"
---
Container models. Prerequisites. The following documentation assumes working knowledge of containerized infrastructure and concepts like container images. If you are unfamiliar with these topics, we recommend reviewing the Docker overview documentation ↗ Foundry allows users to package container images along with a model adapter to create a container-backed Model. The model is then consumable in Foundry as with non-container-backed models. Container-backed models are particularly useful if the models are especially large, pre-trained, written in a language Foundry does not natively support (such as R), or already containerized for other usage. Control Panel houses all features around container governance, including enabling container usage and managing vulnerabilities. If the container setting is not enabled, all Foundry jobs and deployments relying on imported containers will fail. Once container workflows are enabled, the first step is to create a model and begin pushing images into the platform.
