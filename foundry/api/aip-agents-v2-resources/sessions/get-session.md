---
source_url: "https://www.palantir.com/docs/foundry/api/aip-agents-v2-resources/sessions/get-session/"
title: "Get Session \u2022 API Reference"
---
# Get Session

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Get the details of a conversation session between the calling user and an Agent.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:aip-agents-read`.

**operationId:** v2.getSession

**path:** /api/v2/aipAgents/agents/{agentRid}/sessions/{sessionRid}

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

**name:** Session

**example:** {"metadata":{"updatedTime":"2024-10-01T22:04:24.962583055Z","estimatedExpiresTime":"2024-10-02T22:04:24.962583055Z","messageCount":6,"createdTime":"2024-10-01T20:04:24.962583055Z","title":"What is the status of my order?"},"agentRid":"ri.aip-agents..agent.732cd5b4-7ca7-4219-aabb-6e976faf63b1","agentVersion":"1.0","rid":"ri.aip-agents..session.292db3b2-b653-4de6-971c-7e97a7b881d6"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The Resource Identifier (RID) of the conversation session. |
| metadata | objectType | True | Metadata about the session. |
| agentRid | stringType | True | The Resource Identifier (RID) of the Agent associated with the session. |
| agentVersion | stringType | True | The version of the Agent associated with the session. This can be set by clients on session creation. If not specified, defaults to use the latest published version of the Agent at session creation time. |

**example:** {"metadata":{"updatedTime":"2024-10-01T22:04:24.962583055Z","estimatedExpiresTime":"2024-10-02T22:04:24.962583055Z","messageCount":6,"createdTime":"2024-10-01T20:04:24.962583055Z","title":"What is the status of my order?"},"agentRid":"ri.aip-agents..agent.732cd5b4-7ca7-4219-aabb-6e976faf63b1","agentVersion":"1.0","rid":"ri.aip-agents..session.292db3b2-b653-4de6-971c-7e97a7b881d6"}

### Error Responses

| name | description |
| --- | --- |
| SessionNotFound | The given Session could not be found. |
| AgentNotFound | The given Agent could not be found. |
