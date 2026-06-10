---
source_url: "https://www.palantir.com/docs/foundry/private-link/"
title: "Documentation | Private links (VPC connectivity) > Overview"
---
# Overview

The traffic to and from your Foundry enrollment can be routed through the public Internet or through the private network of the cloud provider that hosts your Foundry instance. Private links are cloud provider services for creating private VPC (virtual private cloud) endpoints that allow direct, secure connectivity between your cloud VPCs and the Palantir Foundry VPC without traversing the public Internet.

From the perspective of Palantir Foundry, there are two directions for this traffic:

* *Ingress* from your cloud VPC to Palantir Foundry.
* *Egress* from Palantir Foundry to your cloud VPC.

For detailed instructions on how to set up private links for each of the supported cloud providers, follow the links below:

* [Amazon AWS PrivateLink](/docs/foundry/private-link/aws-private-link/)
* [Microsoft Azure Private Link](/docs/foundry/private-link/azure-private-link/)
* [Google Cloud Platform Private Service Connect](/docs/foundry/private-link/gcp-private-service-connect/)

## Private link supported capabilities

Some private link capabilities are self-serve in Control Panel, some require assistance from a Palantir representative to set up, and some are not yet supported. The table below describes the availability of private link capabilities.

| Cloud Provider  | Traffic Direction | Status | Setup | Documentation | Cloud Region |
|--- |--- |--- |--- |--- |--- |
| AWS | Ingress | 🟢 Available | 🛠️ Manual | [✅ Link](/docs/foundry/private-link/aws-private-link/#ingress-to-foundry-for-aws-privatelink) | Cross-region |
| AWS | Egress | 🟢 Available  | ✨ Automatic in Control Panel | [✅ Link](/docs/foundry/private-link/aws-private-link/#egress-from-foundry-for-aws-privatelink) | Cross-region |
| Azure | Ingress | 🟢 Available | 🛠️ Manual | [✅ Link](/docs/foundry/private-link/azure-private-link/#ingress-to-foundry-for-azure-private-link) | Cross-region |
| Azure | Egress | 🟢 Available | ✨ Automatic in Control Panel | [✅ Link](/docs/foundry/private-link/azure-private-link/#egress-from-foundry-for-azure-private-link) | Cross-region |
| GCP | Ingress | 🟢 Available | 🛠️ Manual | ❌ Not Documented | Cross-region |
| GCP | Egress | 🟢 Available | 🛠️ Manual | ❌ Not Documented | Cross-region |
