---
source_url: "https://www.palantir.com/docs/apollo/apollo-getting-started/"
title: "Documentation | Getting started > Getting started with Apollo"
---
# Getting started with Apollo

To get started, you will need a [working Apollo Hub](/docs/apollo/apollo-getting-started/set-up-your-apollo-hub/).

You should also [review the key Apollo concepts](/docs/apollo/core/introduction/) before following this guide.

:::callout{theme="neutral"}
For hands-on experience with Apollo, we recommend completing the [Apollo Introduction Guide](/docs/apollo/apollo-getting-started/introduction-welcome/).
:::

## 1. Connect an Environment

Apollo uses a Hub-and-Spoke architecture, where your Spoke Environment is a Kubernetes cluster. If you are testing, you can connect a local Kubernetes cluster. Otherwise, you should use a [CNCF-certified distribution of Kubernetes ↗](https://www.cncf.io/certification/software-conformance/#logos).

[Kubernetes production cluster requirements ↗](/docs/apollo/managing-environments/spoke-environment-prerequisites/)

[Set up a local Kubernetes cluster for testing ↗](/docs/apollo/core/set-up-local-kubernetes-cluster/)

[Connect a Kubernetes cluster to Apollo ↗](/docs/apollo/core/connect-spoke/)

## 2. Create a Product

A **Product** is the software that you want to deploy with Apollo.

[Create a new Product ↗](/docs/apollo/managing-products/create-a-new-product/)

[Create a Product Release ↗](/docs/apollo/managing-products/publishing-helm-charts/)

[Create Product Releases in Apollo from your CI pipeline ↗](/docs/apollo/core/ci-publish-setup/)

## 3. Install a Product in your Environment

An **Entity** in Apollo is an installation of a Product in an Environment. Apollo manages monitoring, upgrades, and maintenance for these installations.

[Install software in your Environment ↗](/docs/apollo/managing-entities/add-and-edit-entities/)

## 4. (Optional) Change how Apollo manages your deployed software

Apollo enables [Environment and Product editors](/docs/apollo/core/authorization/) to set requirements that must be satisfied before Apollo undertakes an action, such as an upgrade. Apollo considers the resolved set of Product and Environment requirements before recommending any action.

**Environments**

[Edit Environment management settings ↗](/docs/apollo/managing-environments/editing-environment-management-settings/)

[Edit the Environment settings ↗](/docs/apollo/managing-environments/environment-settings/)

**Products**

[Configure a Release promotion pipeline ↗](/docs/apollo/managing-release-channels/configure-promotion-pipeline/)

[Manually promote Releases ↗](/docs/apollo/managing-release-channels/manual-promotion/)

[Set Product maintenance windows ↗](/docs/apollo/managing-products/product-maintenance-window/)

## 5. Recall and roll-off

**Recalls** are how you communicate to Apollo that there is a problem with one or more Releases. When you issue a recall, Apollo will automatically remediate the issue by blocking bad Releases from further roll-out and installing non-recalled Releases in affected Environments.

[Issue a recall ↗](/docs/apollo/recalling-releases/recall-release/#issue-a-recall)

[Roll your Environments onto a safe Release ↗](/docs/apollo/recalling-releases/roll-off-strategies/)

## 6. SecOps: Vulnerability scanning and SBOMs

Apollo offers several security workflows that provide you full visibility into your security scans and help streamline actions based on the results.

[Manage security workflows ↗](/docs/apollo/managing-vulnerabilities/overview/)
