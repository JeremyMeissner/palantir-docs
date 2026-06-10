---
source_url: "https://www.palantir.com/docs/foundry/api/aip-agents-v2-resources/agents/get-agent/"
title: "Get Agent \u2022 API Reference"
---
# Get Agent

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Get details for an Agent.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:aip-agents-read`.

**operationId:** v2.getAgent

**path:** /api/v2/aipAgents/agents/{agentRid}

### Operation Type

### Scopes

| name |
| --- |
| api:aip-agents-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| agentRid | stringType | True | An RID identifying an Agent created in [AIP Chatbot Studio](/docs/foundry/chatbot-studio/overview/). |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| version | stringType | False | The version of the Agent to retrieve. If not specified, the latest published version will be returned. |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** Agent

**example:** {"metadata":{"displayName":"Supply Chain Support Agent","suggestedPrompts":["What is the status of my order?","How do I track my shipment?"],"description":"An intelligent assistant to help answer questions about supply chain operations.","inputPlaceholder":"Ask about supply chain operations..."},"rid":"ri.aip-agents..agent.732cd5b4-7ca7-4219-aabb-6e976faf63b1","version":"1.0","parameters":{"customerName":{"access":"READ_ONLY","description":"The name of the customer to answer supply chain-related questions for."}}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | An RID identifying an Agent created in [AIP Chatbot Studio](/docs/foundry/chatbot-studio/overview/). |
| version | stringType | True | The version of this instance of the Agent. |
| metadata | objectType | True | Metadata for an Agent. |
| parameters | mapType | False | The types and names of variables configured for the Agent in [AIP Chatbot Studio](/docs/foundry/chatbot-studio/overview/) in the [application state](/docs/foundry/chatbot-studio/application-state/). These variables can be used to send custom values in prompts sent to an Agent to customize and control the Agent's behavior. |

**example:** {"metadata":{"displayName":"Supply Chain Support Agent","suggestedPrompts":["What is the status of my order?","How do I track my shipment?"],"description":"An intelligent assistant to help answer questions about supply chain operations.","inputPlaceholder":"Ask about supply chain operations..."},"rid":"ri.aip-agents..agent.732cd5b4-7ca7-4219-aabb-6e976faf63b1","version":"1.0","parameters":{"customerName":{"access":"READ_ONLY","description":"The name of the customer to answer supply chain-related questions for."}}}

### Error Responses

| name | description |
| --- | --- |
| NoPublishedAgentVersion | Failed to retrieve the latest published version of the Agent because the Agent has no published versions. Try publishing the Agent in AIP Chatbot Studio to use the latest published version, or specify the version of the Agent to use. |
| InvalidAgentVersion | The provided version string is not a valid format for an Agent version. |
| AgentNotFound | The given Agent could not be found. |
| AgentVersionNotFound | The given AgentVersion could not be found. |
