---
source_url: "https://www.palantir.com/docs/foundry/api/aip-agents-v2-resources/contents/get-content/"
title: "Get Content \u2022 API Reference"
---
# Get Content

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Get the conversation content for a session between the calling user and an Agent.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:aip-agents-read`.

**operationId:** v2.getContent

**path:** /api/v2/aipAgents/agents/{agentRid}/sessions/{sessionRid}/content

### Operation Type

### Scopes

| name |
| --- |
| api:aip-agents-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| agentRid | stringType | True | An RID identifying an Agent created in [AIP Chatbot Studio](/docs/foundry/chatbot-studio/overview/). |
| sessionRid | stringType | True | The Resource Identifier (RID) of the conversation session. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** Content

**example:** {"exchanges":[{"result":{"totalTokensUsed":6448,"agentMarkdownResponse":"The status of your order is **In Transit**.","sessionTraceId":"12345678-1234-5678-1234-123456789abc","interruptedOutput":false},"userInput":{"text":"What is the status of my order?"},"contexts":{"objectContexts":[{"objectRids":["ri.phonograph2-objects.main.object.48668bf6-8878-48d2-b8f8-f0017593feb5"],"propertyTypeRids":["ri.ontology.main.property.7899aeb4-a389-4f2e-a0fd-e7193a4f6cb1"]}]}}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| exchanges | listType | False | The conversation history for the session, represented as a list of exchanges. Each exchange represents an initiating message from the user and the Agent's response. Exchanges are returned in chronological order, starting with the first exchange. |

**example:** {"exchanges":[{"result":{"totalTokensUsed":6448,"agentMarkdownResponse":"The status of your order is **In Transit**.","sessionTraceId":"12345678-1234-5678-1234-123456789abc","interruptedOutput":false},"userInput":{"text":"What is the status of my order?"},"contexts":{"objectContexts":[{"objectRids":["ri.phonograph2-objects.main.object.48668bf6-8878-48d2-b8f8-f0017593feb5"],"propertyTypeRids":["ri.ontology.main.property.7899aeb4-a389-4f2e-a0fd-e7193a4f6cb1"]}]}}]}

### Error Responses

| name | description |
| --- | --- |
| ContentNotFound | The given Content could not be found. |
| AgentNotFound | The given Agent could not be found. |
| SessionNotFound | The given Session could not be found. |
