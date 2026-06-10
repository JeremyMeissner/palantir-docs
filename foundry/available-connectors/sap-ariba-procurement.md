---
source_url: "https://www.palantir.com/docs/foundry/available-connectors/sap-ariba-procurement/"
title: "Documentation | SAP applications > SAP Ariba Procurement"
---
# SAP Ariba Procurement

<!-- BEGIN GENERATED:intro -->

The SAP Ariba Procurement connector is a [Palantir-provided driver](/docs/foundry/data-integration/foundry-provided-drivers/) for SAP Ariba Procurement.

To create a new SAP Ariba Procurement source, follow the [standard setup flow for Palantir-provided drivers](/docs/foundry/data-integration/foundry-provided-drivers/#setup), then use the sections below for SAP Ariba Procurement-specific configuration and networking. For the complete property reference, see the [official SAP Ariba Procurement driver documentation ↗](https://cdn.cdata.com/help/PAM/jdbc/pg_connectionj.htm).

<!-- END GENERATED:intro -->

<!-- BEGIN GENERATED:configuration -->

## Configuration

The properties below are mandatory or recommended.

| Property | Required? | Description | Default |
|---|---|---|---|
| [`API` ↗](https://cdn.cdata.com/help/PAM/jdbc/RSBSAPAribaProcurement_p_API.htm) | Mandatory | Specify which API you would like the provider to retrieve SAP Ariba data from. | `PurchaseOrdersBuyerAPI-V1` |
| [`APIKey` ↗](https://cdn.cdata.com/help/PAM/jdbc/RSBSAPAribaProcurement_p_APIKey.htm) | Mandatory | Your OAuth application key. | — |
| [`AuthScheme` ↗](https://cdn.cdata.com/help/PAM/jdbc/RSBSAPAribaProcurement_p_AuthScheme.htm) | Mandatory | Set the type of authentication to use when connecting to SAP Ariba. | `OAuthClient` |
| [`Environment` ↗](https://cdn.cdata.com/help/PAM/jdbc/RSBSAPAribaProcurement_p_Environment.htm) | Recommended | The environment to use when connecting to SAP Ariba. | `PRODUCTION` |
| [`MaxThreads` ↗](https://cdn.cdata.com/help/PAM/jdbc/RSBSAPAribaProcurement_p_MaxThreads.htm) | Recommended | Specifies the maximum number of concurrent requests the provider can execute to SAP Ariba. | `5` |

<!-- END GENERATED:configuration -->

<!-- BEGIN GENERATED:networking -->

## Networking

The table below lists the domains that the source needs to be able to access in order to successfully run.

For each domain, add a corresponding [egress policy](/docs/foundry/administration/configure-egress/). If the source is hosted on-premises and not directly reachable from Foundry, use an [agent proxy egress policy](/docs/foundry/administration/configure-egress/#agent-proxy-egress-policies) instead; the agent host itself must also be able to reach the listed domains. See [using an agent as a proxy](/docs/foundry/data-connection/agent-proxy/) for details.

| Domain  | Required |
|--- |--- |
| openapi.ariba.com | If `DataCenter=US` (default) |
| api.ariba.com | If `DataCenter=US` (default) |
| eu.openapi.ariba.com | If `DataCenter=EU` |
| api-eu.ariba.com | If `DataCenter=EU` |
| ru.openapi.ariba.com | If `DataCenter=RU` |
| api-ru.ariba.com | If `DataCenter=RU` |
| mn1.openapi.ariba.com | If `DataCenter=UAE` |
| api.mn1.ariba.com | If `DataCenter=UAE` |
| mn2.openapi.ariba.com | If `DataCenter=KSA` |
| api.mn2.ariba.com | If `DataCenter=KSA` |
| openapi.sapariba.cn | If `DataCenter=CN` |
| api.sapariba.cn | If `DataCenter=CN` |
| openapi.au.cloud.ariba.com | If `DataCenter=AU` |
| api.au.cloud.ariba.com | If `DataCenter=AU` |
| openapi.jp.cloud.ariba.com | If `DataCenter=JP` |
| api.jp.cloud.ariba.com | If `DataCenter=JP` |

<!-- END GENERATED:networking -->
