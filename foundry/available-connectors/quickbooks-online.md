---
source_url: "https://www.palantir.com/docs/foundry/available-connectors/quickbooks-online/"
parquet_url: "/foundry/available-connectors/quickbooks-online/"
title: "QuickBooks Online"
fetched_at: "2026-05-12T19:34:36.198Z"
---
QuickBooks Online. The QuickBooks Online connector is a Palantir-provided driver connector. The official documentation for this driver can be found here ↗. Networking. The table below lists the domains that the source needs to be able to access in order to successfully run. If running the connection on a Foundry worker, be sure to add corresponding egress policies for each of those domains. If those domains are in a different network from Foundry's network, and you are using agent proxy egress policies (preferred) or an agent worker (not recommended), the agent must be able to reach the domain addresses. Additionally, the systems on those domains must be configured to allow connections from the agent. Learn more about agent networking. DomainRequired quickbooks.api.intuit.com. If UseSandbox=FALSE (Default). sandbox-quickbooks.api.intuit.com. If UseSandbox=TRUE. qbo.sbfice.intuit.com. Used when retrieving Entitlements (only available when UseSandbox=FALSE). appcenter.intuit.com. Authorization URL. developer.api.intuit.com. Always. May be used for token disconnects. oauth.platform.intuit.com. Always. Token URL.
