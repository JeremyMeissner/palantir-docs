---
source_url: "https://www.palantir.com/docs/apollo/managing-artifact-registries/"
title: "Documentation | Managing Artifact Registries > Overview"
---
# Managing Artifact Registries

Apollo supports directly integrating with an existing OCI registry to allow the management and deployment of software directly from your registry. Instead of publishing containers for Product Releases directly to Apollo's Container Registry, you can link your existing OCI registry to Apollo and create Product Releases in Apollo that reference artifacts from your own OCI Registry. Then, you can assign this Artifact Registry to an Environment and the Products will be deployable to that Environment. Apollo's vulnerability scanning will also scan images from connected Artifact Registries.

Apollo supports the following OCI registries:

* Registries that do not require authentication
* OCI compliant registries that use basic authentication
* Amazon Elastic Container Registry (ECR)

## Getting started

* [Create an Artifact Registry](/docs/apollo/managing-artifact-registries/create-artifact-registry/)
* [Assign an Artifact Registry to an Environment](/docs/apollo/managing-artifact-registries/assign-artifact-registry/)
