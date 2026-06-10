---
source_url: "https://www.palantir.com/docs/foundry/available-connectors/microsoft-sharepoint/"
title: "Documentation | Available connectors > Microsoft SharePoint"
---
# Microsoft SharePoint

<!-- BEGIN GENERATED:intro -->

The Microsoft SharePoint connector is a [Palantir-provided driver](/docs/foundry/data-integration/foundry-provided-drivers/) for Microsoft SharePoint.

To create a new Microsoft SharePoint source, follow the [standard setup flow for Palantir-provided drivers](/docs/foundry/data-integration/foundry-provided-drivers/#setup), then use the sections below for Microsoft SharePoint-specific configuration and networking. For the complete property reference, see the [official Microsoft SharePoint driver documentation ↗](https://cdn.cdata.com/help/RSJ/jdbc/).

<!-- END GENERATED:intro -->

<!-- BEGIN GENERATED:configuration -->

## Configuration

The properties below are mandatory or recommended.

| Property | Required? | Description | Default |
|---|---|---|---|
| `Schema` | Mandatory | Specifies the type of schema the provider uses for connecting to Microsoft SharePoint. | `SOAP` |
| [`URL` ↗](https://cdn.cdata.com/help/RSJ/jdbc/RSBSharePoint_p_URL.htm) | Mandatory | Specifies the base URL of the Microsoft SharePoint site to connect to. This URL is used as the starting point for all API calls. | `https://teams.contoso.com` |
| [`AuthScheme` ↗](https://cdn.cdata.com/help/RSJ/jdbc/RSBSharePoint_p_AuthScheme.htm) | Recommended | Specifies the authentication scheme used to connect to Microsoft SharePoint. | `AzurePassword` |
| [`AzureTenant` ↗](https://cdn.cdata.com/help/RSJ/jdbc/RSBSharePoint_p_AzureTenant.htm) | Recommended | Identifies the Microsoft SharePoint tenant being used to access data. Accepts either the tenant's domain name (for example, contoso.onmicrosoft.com ) or its directory (tenant) ID. | — |
| [`Password` ↗](https://cdn.cdata.com/help/RSJ/jdbc/RSBSharePoint_p_Password.htm) | Recommended | Specifies the password used to authenticate the user. | — |
| [`SharePointEdition` ↗](https://cdn.cdata.com/help/RSJ/jdbc/RSBSharePoint_p_SharePointEdition.htm) | Recommended | Specifies the Microsoft SharePoint edition to connect to. | `SharePoint Online` |
| [`User` ↗](https://cdn.cdata.com/help/RSJ/jdbc/RSBSharePoint_p_User.htm) | Recommended | Specifies the Microsoft SharePoint user account used for authentication. | `username@domain.onmicrosoft.com` |

<!-- END GENERATED:configuration -->

<!-- BEGIN GENERATED:networking -->

## Networking

The table below lists the domains that the source needs to be able to access in order to successfully run.

For each domain, add a corresponding [egress policy](/docs/foundry/administration/configure-egress/). If the source is hosted on-premises and not directly reachable from Foundry, use an [agent proxy egress policy](/docs/foundry/administration/configure-egress/#agent-proxy-egress-policies) instead; the agent host itself must also be able to reach the listed domains. See [using an agent as a proxy](/docs/foundry/data-connection/agent-proxy/) for details.

| Domain  | Required |
|--- |--- |
| \<URL> | Always. URL connection property |
| \<KerberosKDC>:88 | If `SharePointEdition='SharePoint OnPremise'` (default) AND `AuthScheme=Negotiate` |
| \<KerberosServiceKDC>:88 | If `SharePointEdition='SharePoint OnPremise'` (default) AND `AuthScheme=Negotiate` AND Kerberos topology uses multiple realms |
| \<SSOLoginURL> | If `SharePointEdition='SharePoint OnPremise'` (default) AND `AuthScheme=ADFS` |
| login.microsoftonline.com | If `SharePointEdition='SharePoint Online'` AND `AuthScheme=AzureAD,` AzurePassword, SharePointOAuth, OAuthJWT  AND `AzureEnvironment=GLOBAL` (default) |
| login.chinacloudapi.cn | If `SharePointEdition='SharePoint Online'` AND `AuthScheme=AzureAD,` AzurePassword, SharePointOAuth, OAuthJWT AND `AzureEnvironment=CHINA` |
| login.microsoftonline.us | If `SharePointEdition='SharePoint Online'` AND `AuthScheme=AzureAD,` AzurePassword, SharePointOAuth, OAuthJWT AND `AzureEnvironment=USGOVT` or USGOVTDOD |

<!-- END GENERATED:networking -->
