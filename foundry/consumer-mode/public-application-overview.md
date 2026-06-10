---
source_url: "https://www.palantir.com/docs/foundry/consumer-mode/public-application-overview/"
title: "Documentation | Public Applications > What are Public Applications?"
---
# What are Public Applications?

A **Public Application** is a Foundry-hosted website paired with a constrained, allow-listed unauthenticated ontology API, both served from a Foundry subdomain. Public Applications enable developers to build internet-facing experiences directly on Foundry, without exporting data to an external hosting platform. The Public Application's end users do not log in to Foundry, so anyone who can reach the subdomain can load the website and call the small set of unauthenticated ontology operations it exposes. Foundry handles authentication on their behalf through a service user managed by the application.

:::callout{theme="neutral" title="Looking for the Slate public form upload feature?"}
This page documents OSDK-based Public Applications served from [Developer Console](/docs/foundry/developer-console/overview/). If you are looking for the Slate-based public form upload workflow, see [Upload data for public applications](/docs/foundry/slate/public-applications-data-upload/).
:::

## When to use a Public Application

Public Applications support workflows where the end users are members of the public who do not, and should not, have a Foundry account. Common patterns include:

* **One-way data collection forms:** Send a link to members of the public so they can submit information, where each submission is stored in the ontology through a non-function-backed action and users do not require return access to the data they submit.
* **Public data dissemination dashboards:** Present pre-computed aggregate views of your ontology's data and allow limited end-user interaction, such as filtering by a known dimension.
* **Public registration and sign-up flows:** Collect interest, contact details, or registration information from a known audience without requiring those users to onboard to Foundry.
* **Static website landing pages:** Deploy landing pages that do not require interaction with your ontology at all.

## Public Application structure

Foundry composes a Public Application as three customer-visible parts:

1. **Unauthenticated website:** The static assets (HTML, CSS, and JavaScript) of your application are served from a Foundry subdomain without requiring a Foundry login. This is similar to a [Foundry-hosted OSDK application](/docs/foundry/developer-console/deploy-custom-application-on-foundry/) *without* the login flow.
2. **OSDK in the end user's browser:** Your application uses the [OSDK](/docs/foundry/developer-console/overview/) to make ontology calls from the user's browser, using only operations that you explicitly enable for unauthenticated access.
3. **Unauthenticated API proxy:** Each ontology call from the browser is routed through a Foundry-managed proxy that authenticates the request as the application's service user before it reaches the ontology. The end user never holds, sees, or transmits a Foundry token.

Public Applications perform every request as the application's service user, so the Public Application's resource scope [configured in Developer Console](/docs/foundry/developer-console/application-restrictions/) and resources visible to the service user define the maximum surface area of data it can expose.

:::callout{theme="neutral"}
A Public Application can be composed of *only* an **Unauthenticated website** or a *combination of* an **Unauthenticated website** and an **Unauthenticated API proxy**.
:::

## Security and protection model

Foundry exposes Public Applications to your enrollment's [ingress policies](/docs/foundry/administration/configure-ingress/), which may be as broad as the open internet without authentication, so Foundry applies several protections by default. Developers cannot configure these default protections, as they exist to ensure enrollment stability and limit potential abuse.

### Strict allow-list of ontology operations

You can only call a small subset of ontology operations from a Public Application. Foundry blocks any operation at the proxy layer regardless of the calling user's permissions that triggers non-constant compute, including functions, function-backed actions, search, aggregation, and search-arounds. Review [the currently supported features documentation](/docs/foundry/consumer-mode/public-application-supported-features/) for the full list of blocked operations.

### Per-application rate limits

Foundry applies per-application rate limits to unauthenticated traffic before any authentication swap is performed. This protects the rest of the platform from abuse on the public internet and ensures that one application's traffic cannot exhaust the capacity of another.

### Inherited ingress and Web Application Firewall (WAF) protection

A Public Application's subdomain inherits the ingress policy of the parent enrollment domain. If your enrollment is restricted to a specific set of regions or networks (for example, US-only), the same restrictions apply to the Public Application. All requests pass through the enrollment WAF before reaching Foundry. Foundry offers individual application ingress policy configuration to allow for Public Applications to serve broader ingress policies compared to the enrollment.

### Service user identity only

The application runs as a **service user** managed by Foundry. There is no per-end-user identity in a Public Application, so Foundry cannot, for example, attribute a write back to an individual member of the public. You should not use a Public Application for workflows that require per-end-user identity. For background on service users and the client credentials grant, review the [OAuth2 clients documentation](/docs/foundry/platform-security-third-party/writing-oauth2-clients/).

## Resource governance

You can only add a resource to a Public Application if you have permission to remove every [Marking](/docs/foundry/platform-security-management/manage-markings/) and [Organization Marking](/docs/foundry/platform-security-management/manage-orgs-and-spaces/) on that resource. If you cannot, then Foundry blocks you from adding a resource to the application's scope.

This export control model ensures that resources only become reachable from the public internet through an explicit, audited decision-making process made by someone who already has the authority to lift each restriction on the data.

[Learn more about Markings in Foundry.](/docs/foundry/security/markings/)

## How to mitigate risks when creating and exposing Public Applications

Public Applications can be configured to be reachable by anyone on the internet without authentication, so you as the application developer are responsible for implementing the risk mitigation practices outlined in the sections below *in addition to* the Foundry-managed protections described above.

### Ensure URL identifiers are unguessable

Anything served by a Public Application is reachable by anyone who can access the URL and meets the enrollment's ingress policies. You should ensure that identifiers in URLs are unguessable (for example, randomly generated UUIDs). Only data that is intentionally publishable should be in scope.

### Eliminate compute exposure

Function-driven workflows are blocked today specifically because they may expose enrollments to compute-cost attacks. If your workflow needs heavier processing, perform it asynchronously inside Foundry. As an example, configure an [automation](/docs/foundry/automate/overview/) on data already written by the application rather than attempting to run it on-demand from a Public Application.

### Ensure all resources exposed can be made public

Adding a resource to a Public Application makes the resource reachable from the public internet. You are responsible for ensuring that the resources added are intended to be public and for treating each addition as an export decision.

## Approval requirements

Every Public Application requires a use-case review by an **Information Security Officer** in your enrollment before it can be enabled. The **Information Security Officer** is responsible for confirming that:

* The intended workflow is appropriate for an internet-facing, unauthenticated surface.
* The resources added to the application are intended to be reachable from the public internet.
* You, as the developer, understand the [risks](#how-to-mitigate-risks-when-creating-and-exposing-public-applications) and have designed the workflow to mitigate them.

This review occurs *in addition to* the standard subdomain approval that the same role performs in [Control Panel](/docs/foundry/administration/control-panel/) as part of [the Public Application setup process](/docs/foundry/consumer-mode/public-application-setup/). Document the approved use case before requesting the subdomain so the approver has the context needed to make the decision.

## Next steps

Now that you have an understanding of what Public Applications are and how users interact with them outside of Foundry, you can [create your first Public Application and configure its subdomain](/docs/foundry/consumer-mode/public-application-setup/).
