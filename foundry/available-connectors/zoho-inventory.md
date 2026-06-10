---
source_url: "https://www.palantir.com/docs/foundry/available-connectors/zoho-inventory/"
title: "Zoho Inventory"
---
# Zoho Inventory

The Zoho Inventory connector is a Palantir-provided driver connector. The official documentation for this driver can be found here ↗. Networking. The table below lists the domains that the source needs to be able to access in order to successfully run. If running the connection on a Foundry worker, be sure to add corresponding egress policies for each of those domains. If those domains are in a different network from Foundry's network, and you are using agent proxy egress policies (preferred) or an agent worker (not recommended), the agent must be able to reach the domain addresses. Additionally, the systems on those domains must be configured to allow connections from the agent. Learn more about agent networking. DomainRequired inventory.zoho.<Region> Always. Region connection property maps to TLD (default Region=US --> .com). <AccountsServer> - default: accounts.zoho.<Region> Always. Retrieved automatically with OAuth flow; set in AccountsServer connection property when manually providing OAuthAccessToken. Region Mappings. Use the following region mapping to complete the domain url: RegionEndpoint US. .com. Europe. .eu. India. .in. Australia. .com.au.
