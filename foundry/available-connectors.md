---
source_url: "https://www.palantir.com/docs/foundry/available-connectors/"
title: "Documentation | Available connectors > Act! CRM"
---
# Act! CRM

<!-- BEGIN GENERATED:intro -->

The Act! CRM connector is a [Palantir-provided driver](/docs/foundry/data-integration/foundry-provided-drivers/) for Act! CRM.

To create a new Act! CRM source, follow the [standard setup flow for Palantir-provided drivers](/docs/foundry/data-integration/foundry-provided-drivers/#setup), then use the sections below for Act! CRM-specific configuration and networking. For the complete property reference, see the [official Act! CRM driver documentation ↗](https://cdn.cdata.com/help/FTK/jdbc/pg_connectionj.htm).

<!-- END GENERATED:intro -->

<!-- BEGIN GENERATED:configuration -->

## Configuration

The properties below are mandatory or recommended.

| Property | Required? | Description | Default |
|---|---|---|---|
| [`ActDatabase` ↗](https://cdn.cdata.com/help/FTK/jdbc/RSBActCRM_p_ActDatabase.htm) | Mandatory | The Act! Database to connect to. | — |
| [`ActEdition` ↗](https://cdn.cdata.com/help/FTK/jdbc/RSBActCRM_p_ActEdition.htm) | Mandatory | The edition of ActCRM being used. Set either Act CRM or Act Premium Cloud. | `Act CRM` |
| [`Password` ↗](https://cdn.cdata.com/help/FTK/jdbc/RSBActCRM_p_Password.htm) | Mandatory | Specifies the password of the authenticating user account. | — |
| [`User` ↗](https://cdn.cdata.com/help/FTK/jdbc/RSBActCRM_p_User.htm) | Mandatory | Specifies the user ID of the authenticating Act! CRM user account. | — |
| [`IncludeCustomFields` ↗](https://cdn.cdata.com/help/FTK/jdbc/RSBActCRM_p_IncludeCustomFields.htm) | Recommended | A boolean indicating if you would like to include custom fields in the column listing. | `TRUE` |
| [`URL` ↗](https://cdn.cdata.com/help/FTK/jdbc/RSBActCRM_p_URL.htm) | Recommended | The URL of the ActCRM account. | `https://apius.act.com` |

<!-- END GENERATED:configuration -->

<!-- BEGIN GENERATED:networking -->

## Networking

The table below lists the domains that the source needs to be able to access in order to successfully run.

For each domain, add a corresponding [egress policy](/docs/foundry/administration/configure-egress/). If the source is hosted on-premises and not directly reachable from Foundry, use an [agent proxy egress policy](/docs/foundry/administration/configure-egress/#agent-proxy-egress-policies) instead; the agent host itself must also be able to reach the listed domains. See [using an agent as a proxy](/docs/foundry/data-connection/agent-proxy/) for details.

| Domain  | Required |
|--- |--- |
| \<URL> | When `ActEdition='Act CRM'` (default) - URL connection property |
| apius.act.com | When `ActEdition='Act Premium Cloud'` and `ActCloudRegion='US'` |
| apiuk.act.com | When `ActEdition='Act Premium Cloud'` and `ActCloudRegion='UK'` |
| apiau.act.com | When `ActEdition='Act Premium Cloud'` and `ActCloudRegion='AUS'` or 'NZ' |
| apieu.act.com | When `ActEdition='Act Premium Cloud'` and `ActCloudRegion='EU'` or 'InternationalEnglish' |

<!-- END GENERATED:networking -->
