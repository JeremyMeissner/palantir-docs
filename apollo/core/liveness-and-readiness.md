---
source_url: "https://www.palantir.com/docs/apollo/core/liveness-and-readiness/"
title: "Liveness and Readiness"
---
# Liveness and Readiness

Apollo automatically collects liveness and readiness from managed Environments using Kubernetes probes. For more information about how to configure these probes, review the Kubernetes documentation ↗. Liveness. Liveness probes are defined to be able to understand whether a service instance (such as a container pod in Kubernetes) is running. Usually, these probes are configured to perform regular checks against service instances (such as HTTP requests or gRPC requests). Failing liveness probes indicate that the service instance has reached a state where it is unusable and needs to be restarted. Readiness. Readiness probes enable service owners to tell the infrastructure when their service is ready to accept network traffic after service start-up. This is useful usually when services need time to perform some startup actions like initiating database connections before accepting network requests. Configuration in Kubernetes. When running in Kubernetes Environments, Apollo supports retrieving liveness and readiness information about your workloads from Kubernetes and exposing it to users in the Apollo Hub. This information is collected automatically from every Entity that is managed by Apollo.
