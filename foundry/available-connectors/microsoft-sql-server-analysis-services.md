---
source_url: "https://www.palantir.com/docs/foundry/available-connectors/microsoft-sql-server-analysis-services/"
parquet_url: "/foundry/available-connectors/microsoft-sql-server-analysis-services/"
title: "Microsoft SQL Server Analysis Services"
fetched_at: "2026-05-12T19:34:36.148Z"
---
Microsoft SQL Server Analysis Services. The Microsoft SQL Server Analysis Services connector is a Palantir-provided driver connector. The official documentation for this driver can be found here ↗. Networking. The table below lists the domains that the source needs to be able to access in order to successfully run. If running the connection on a Foundry worker, be sure to add corresponding egress policies for each of those domains. If those domains are in a different network from Foundry's network, and you are using agent proxy egress policies (preferred) or an agent worker (not recommended), the agent must be able to reach the domain addresses. Additionally, the systems on those domains must be configured to allow connections from the agent. Learn more about agent networking. DomainRequired <URL> Always. URL connection property. <KerberosKDC>:88. If AuthScheme=Negotiate. <KerberosServiceKDC>:88. If AuthScheme=Negotiate AND Kerberos topology uses multiple reams.
