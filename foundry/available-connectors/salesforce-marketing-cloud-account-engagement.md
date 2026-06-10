---
source_url: "https://www.palantir.com/docs/foundry/available-connectors/salesforce-marketing-cloud-account-engagement/"
title: "Salesforce Marketing Cloud Account Engagement"
---
# Salesforce Marketing Cloud Account Engagement

The Salesforce Marketing Cloud Account Engagement connector is a Palantir-provided driver connector. The official documentation for this driver can be found here ↗. Networking. The table below lists the domains that the source needs to be able to access in order to successfully run. If running the connection on a Foundry worker, be sure to add corresponding egress policies for each of those domains. If those domains are in a different network from Foundry's network, and you are using agent proxy egress policies (preferred) or an agent worker (not recommended), the agent must be able to reach the domain addresses. Additionally, the systems on those domains must be configured to allow connections from the agent. Learn more about agent networking. DomainRequired pi.pardot.com. If IsDemoAccount=FALSE (default). pi.demo.pardot.com. If IsDemoAccount=TRUE. login.salesforce.com. If UseSalesforceSandbox=FALSE (default). <Site>.my.salesforce.com. Always. URL returned by API after authentication. test.salesforce.com. If UseSalesforceSandbox=TRUE.
