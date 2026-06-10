---
source_url: "https://www.palantir.com/docs/foundry/consumer-mode/"
title: "Documentation | Consumer mode > Overview"
---
# Consumer mode

Consumer mode allows you to configure Foundry so that users can access specific applications without broader access to the Foundry platform. Consumer mode is particularly useful for building business-to-consumer (B2C) and business-to-business (B2B) applications where external users need access to data and workflows without full platform access.

Rather than a singular solution, consumer mode is a way to configure Foundry such that consumer users, builders, and administrators can only access the features and applications appropriate to their roles.

* Consumer users can only access target applications and necessary resources.
* Consumer user API access is restricted to only include their specific needs.
* Consumer users should never see the Foundry login page, or they should be automatically redirected if already authenticated.
* Builders can leverage Marketplace for release management.
* Builder administrators can enforce that consumers never receive roles beyond the consumer role.

## Consumer application solutions

Foundry supports four types of consumer-facing application configurations:

### In-platform consumer applications

A Workshop, Slate, or Carbon application with restricted platform access.

* **Recommended use:** Build low-code custom applications. Iterate quickly using low-code application builders, and deploy to customers with minimal maintenance burden once built.
* **User login experience:** Login flow which supports automatic redirect to a specific identity provider to avoid multiple login screens.

### OAuth applications

An authorization grant OAuth application hosted within Foundry.

* **Recommended use:** Build pro-code applications hosted in Foundry, leveraging Foundry security primitives for interactive custom applications.
* **User login experience:** Login flow uses OAuth with configurable user consent forms.
* **Hosting:** Foundry subdomains (for example, `https://subdomain-for-app.your-foundry-domain.com/`).

### Client credentials applications

An OAuth/OSDK application hosted externally using a client credentials flow.

* **Recommended use:** Build pro-code applications for maximal user scale that requires customer-defined user authentication and authorization logic outside of Foundry.
* **User login experience:** Application builders must fully own the login experience.
* **Hosting:** External hosting environment with API access to Foundry.

### Public Applications

A pro-code OSDK application served from a Foundry subdomain that does not require any end-user authentication. End users interact with a constrained, allow-listed set of ontology operations through a service user managed by Foundry.

* **Recommended use:** Build internet-facing experiences for users who do not have, and should not need, a Foundry account, such as data collection forms, data dissemination dashboards, and registration flows.
* **User login experience:** No login. Anyone reaching the subdomain can use the application.
* **Hosting:** Foundry subdomains (for example, `https://subdomain-for-app.your-foundry-domain.com/`).
* **Approval requirements:** Each Public Application requires use-case review and approval by an **Information Security Officer** in your enrollment before it can be enabled. [Learn more about Public Applications.](/docs/foundry/consumer-mode/public-application-overview/)

## Consumer mode considerations

### Scale: Ensure your solution meets your needs

Palantir platform-managed authentication and authorization supports the following metrics:

* **User capacity:** 500,000+ users
* **User onboarding:** Up to 5,000 new users per hour
* **Organization limits:** Five organizations per enrollment by default

A client credentials application manages authentication and authorization outside Foundry; only [API limits](https://www.palantir.com/docs/foundry/api/v2/general/overview/limits/) apply.

### Seamless login: Prevent unnecessary authentication

Consumer mode supports a seamless login experience:

* **Default IDP per domain:** Automatic redirect to a configured identity provider.
* **Realm parameter support:** Directly link to an identity provider using `?_realm=realmId` when multiple identity providers are configured for a single domain.
* **Service users:** Service-to-service authentication using client credentials for API access without per-user login requirements.

### Security: Configure access and prevent platform exposure

Consumer mode security operates on multiple levels:

#### Application access restrictions

* **Platform access control:** Disable broader Foundry platform access for consumer organizations.
* **Application-specific access:** Grant access only to Workshop, Slate, or Carbon applications.

#### API access restrictions

* **Role-based permissions:** Enforce minimal permissions necessary for application functionality.
* **Service user permissions:** For client credentials, manage authorization through service user roles.

#### Organization visibility control

* **User and group isolation:** Prevent consumers from discovering other users or groups within the organization.
* **Cross-organization restrictions:** Limit visibility and collaboration between consumer and internal organizations users and groups.

## Getting started

### Step 1: Set up Foundry for consumer usage

:::callout{theme="neutral"}
Foundry platform setup is only required when using Foundry user permissions and authentication. If you are only creating client credentials applications, you can skip this step.
:::

Review our documentation to [configure your Foundry enrollment for consumer mode](/docs/foundry/consumer-mode/foundry-consumer-setup/).

### Step 2: Configure your consumer application

1. [In-platform consumer application](/docs/foundry/consumer-mode/workspace-application-setup/)
2. [OAuth application](/docs/foundry/consumer-mode/oauth-application-setup/)
3. [Client credentials application](/docs/foundry/consumer-mode/client-credentials-setup/)
4. [Public Application](/docs/foundry/consumer-mode/public-application-overview/)
