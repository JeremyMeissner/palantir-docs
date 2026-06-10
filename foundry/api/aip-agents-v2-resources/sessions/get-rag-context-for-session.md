---
source_url: "https://www.palantir.com/docs/foundry/api/aip-agents-v2-resources/sessions/get-rag-context-for-session/"
title: "Get Rag Context For Session \u2022 API Reference"
---
# Get Rag Context For Session

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Retrieve relevant [context](/docs/foundry/chatbot-studio/core-concepts/#retrieval-context) for a user message from the data sources configured for the session.
This allows clients to pre-retrieve context for a user message before sending it to the Agent with the `contextsOverride` option when continuing a session, to allow any pre-processing of the context before sending it to the Agent.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:aip-agents-write`.

**operationId:** v2.getRagContextForSession

**path:** /api/v2/aipAgents/agents/{agentRid}/sessions/{sessionRid}/ragContext

### Operation Type

### Scopes

| name |
| --- |
| api:aip-agents-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| agentRid | stringType | True | An RID identifying an Agent created in [AIP Chatbot Studio](/docs/foundry/chatbot-studio/overview/). |
| sessionRid | stringType | True | The Resource Identifier (RID) of the conversation session. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Request

#### Body

**name:** GetRagContextForSessionRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| userInput | objectType | True | The user message to retrieve relevant context for from the configured Agent data sources. |
| parameterInputs | mapType | False | Any values for [application variables](/docs/foundry/chatbot-studio/application-state/) to use for the context retrieval. |

**example:** {"userInput":{"text":"What is the status of my order?"},"parameterInputs":{"customerName":{"type":"string","value":"Titan Technologies"}}}

### Response

#### Body

Context retrieved from an Agent's configured context data sources which was relevant to the supplied user message.

**name:** AgentSessionRagContextResponse

**example:** {"objectContexts":[{"objectRids":["ri.phonograph2-objects.main.object.48668bf6-8878-48d2-b8f8-f0017593feb5"],"propertyTypeRids":["ri.ontology.main.property.7899aeb4-a389-4f2e-a0fd-e7193a4f6cb1"]}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| objectContexts | listType | False |  |
| functionRetrievedContexts | listType | False |  |

**example:** {"objectContexts":[{"objectRids":["ri.phonograph2-objects.main.object.48668bf6-8878-48d2-b8f8-f0017593feb5"],"propertyTypeRids":["ri.ontology.main.property.7899aeb4-a389-4f2e-a0fd-e7193a4f6cb1"]}]}

### Error Responses

| name | description |
| --- | --- |
| ObjectTypeIdsNotFound | Some object types are configured for use by the Agent but could not be found. The object types either do not exist or the client token does not have access. Object types can be checked by listing available object types through the API, or searching in [Ontology Manager](/docs/foundry/ontology-manager/overview/). |
| ObjectTypeRidsNotFound | Some object types are configured for use by the Agent but could not be found. The object types either do not exist or the client token does not have access. Object types can be checked by listing available object types through the API, or searching in [Ontology Manager](/docs/foundry/ontology-manager/overview/). |
| FunctionLocatorNotFound | The specified function locator is configured for use by the Agent but could not be found. The function type or version may not exist or the client token does not have access. |
| OntologyEntitiesNotFound | Some ontology types are configured for use by the Agent but could not be found. The types either do not exist or the client token does not have access. Object types and their link types can be checked by listing available object/link types through the API, or searching in [Ontology Manager](/docs/foundry/ontology-manager/overview/). |
| GetRagContextForSessionPermissionDenied | Could not ragContext the Session. |
| SessionNotFound | The given Session could not be found. |
| AgentNotFound | The given Agent could not be found. |
