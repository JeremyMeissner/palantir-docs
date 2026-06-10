---
source_url: "https://www.palantir.com/docs/foundry/private-link/customer-owned-domain-private-link/"
parquet_url: "/foundry/private-link/customer-owned-domain-private-link/"
title: "Customer-owned domain with private link"
fetched_at: "2026-05-12T19:34:36.984Z"
---
Customer-owned domain with private link. If you have set up a private link to your Foundry environment, and if the Foundry domain is owned by you (meaning that the domain is not a Palantir-owned domain, such as *.palantirfoundry.com), there is additional configuration needed to funnel internal Foundry services through the endpoint. Follow these steps to complete configuration of a private link for a customer-owned domain: Provision a separate secondary domain that will be used for internal Foundry container services. This can also be a subdomain of the main Foundry domain, such as containers.foundry.<customer>.com. Set up a DNS C-Name to point this secondary domain to the VPC Endpoint Universal DNS name, the same as for the main Foundry domain. Sign and return the Certificate Signing Request (CSR) for the secondary domain provided by a Palantir representative. Palantir will configure the Foundry instance to serve the new certificate for the secondary domain. After this is done, all traffic to Foundry will be routed through the private link that was set up.
