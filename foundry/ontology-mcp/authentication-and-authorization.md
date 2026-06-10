---
source_url: "https://www.palantir.com/docs/foundry/ontology-mcp/authentication-and-authorization/"
title: "Documentation | Ontology MCP > Authentication and authorization"
---
# Authentication and authorization

Ontology MCP (OMCP) is built on top of the OAuth 2.0 configuration of the [Developer Console application](/docs/foundry/developer-console/overview/) that exposes it. When an MCP client connects to your Ontology MCP server, it authenticates using the same OAuth 2.0 client and authorization server that handle all other requests to your application; there is no separate authentication system to configure for MCP.

The [application restrictions](/docs/foundry/developer-console/application-restrictions/), [permissions](/docs/foundry/developer-console/permissions/), and OAuth client settings you have already defined for your Developer Console application also apply to requests made through Ontology MCP. Tokens issued for MCP access are scoped to the operations and resources you have granted to the application.

## Supported grant types

Ontology MCP supports the two OAuth 2.0 grant types that Foundry exposes for third-party applications. Choose the grant type that matches how your MCP client will act on behalf of users:

* **[Authorization code grant](/docs/foundry/platform-security-third-party/writing-oauth2-clients/#authorization-code-grant):** Use this grant type when the MCP client should act on behalf of an end user. Each user explicitly consents to the requested scopes, and the resulting access token is scoped to that user's permissions in Foundry. This is the appropriate choice for interactive agents and editors where individual users sign in to access ontology resources.
* **[Client credentials grant](/docs/foundry/platform-security-third-party/writing-oauth2-clients/#client-credentials-grant):** Use this grant type for non-interactive, service-to-service workflows where the MCP client acts as a service user rather than on behalf of a specific end user. The client authenticates with a client ID and client secret, so it must be a confidential client capable of safely storing the secret. This is the appropriate choice for backend services and integrations such as [Microsoft Copilot Studio](/docs/foundry/ontology-mcp/mcp-tools-and-agent-configuration/#microsoft-copilot-studio-integration).

You can enable one or both grant types on the same Developer Console application, depending on the MCP clients you intend to support. Configure the redirect URLs, scopes, and client secrets for each grant type from the **OAuth & Permissions** page of your application in Developer Console.

For a full description of the OAuth 2.0 flows, endpoints, and parameters that Foundry supports, see [Writing OAuth2 clients for Foundry](/docs/foundry/platform-security-third-party/writing-oauth2-clients/).

## Scopes and restrictions

Access tokens issued to MCP clients are restricted by the [scopes](/docs/foundry/developer-console/application-restrictions/) configured on your Developer Console application. Make sure that the application is granted the operations required by the ontology resources that you expose through MCP, and that the requesting user or service user has the necessary [permissions](/docs/foundry/developer-console/permissions/) on the underlying objects, actions, and queries.
