---
source_url: "https://www.palantir.com/docs/foundry/api/aip-agents-v2-resources/sessions/create-session/"
title: "Create Session \u2022 API Reference"
---
# Create Session

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Create a new conversation session between the calling user and an Agent.
Use `blockingContinue` or `streamingContinue` to start adding exchanges to the session.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:aip-agents-write`.

**operationId:** v2.createSession

**path:** /api/v2/aipAgents/agents/{agentRid}/sessions

### Operation Type

### Scopes

| name |
| --- |
| api:aip-agents-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| agentRid | stringType | True | An RID identifying an Agent created in [AIP Chatbot Studio](/docs/foundry/chatbot-studio/overview/). |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** CreateSessionRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| agentVersion | stringType | False | The version of the Agent associated with the session. This can be set by clients on session creation. If not specified, defaults to use the latest published version of the Agent at session creation time. |

**example:** {"agentVersion":"1.0"}

### Response

#### Body

The created Session

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
| NoPublishedAgentVersion | Failed to retrieve the latest published version of the Agent because the Agent has no published versions. Try publishing the Agent in AIP Chatbot Studio to use the latest published version, or specify the version of the Agent to use. |
| ObjectTypeIdsNotFound | Some object types are configured for use by the Agent but could not be found. The object types either do not exist or the client token does not have access. Object types can be checked by listing available object types through the API, or searching in [Ontology Manager](/docs/foundry/ontology-manager/overview/). |
| ObjectTypeRidsNotFound | Some object types are configured for use by the Agent but could not be found. The object types either do not exist or the client token does not have access. Object types can be checked by listing available object types through the API, or searching in [Ontology Manager](/docs/foundry/ontology-manager/overview/). |
| FunctionLocatorNotFound | The specified function locator is configured for use by the Agent but could not be found. The function type or version may not exist or the client token does not have access. |
| InvalidAgentVersion | The provided version string is not a valid format for an Agent version. |
| OntologyEntitiesNotFound | Some ontology types are configured for use by the Agent but could not be found. The types either do not exist or the client token does not have access. Object types and their link types can be checked by listing available object/link types through the API, or searching in [Ontology Manager](/docs/foundry/ontology-manager/overview/). |
| CreateSessionPermissionDenied | Could not create the Session. |
| AgentNotFound | The given Agent could not be found. |
| AgentVersionNotFound | The given AgentVersion could not be found. |
| SessionNotFound | The given Session could not be found. |
