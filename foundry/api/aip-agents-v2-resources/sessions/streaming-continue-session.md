---
source_url: "https://www.palantir.com/docs/foundry/api/aip-agents-v2-resources/sessions/streaming-continue-session/"
title: "Streaming Continue Session \u2022 API Reference"
---
# Streaming Continue Session

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Continue a conversation session with an Agent, or add the first exchange to a session after creation.
Adds a new exchange to the session with the provided inputs, and generates a response from the Agent.
Returns a stream of the Agent response text (formatted using markdown) for clients to consume as the response is generated.
On completion of the streamed response, clients can load the full details of the exchange that was added to the session by reloading the session content.
Streamed exchanges also support cancellation; see `cancel` for details.
Concurrent requests to continue the same session are not supported.
Clients should wait to receive a response, or cancel the in-progress exchange, before sending the next message.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:aip-agents-write`.

**operationId:** v2.streamingContinueSession

**path:** /api/v2/aipAgents/agents/{agentRid}/sessions/{sessionRid}/streamingContinue

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

**name:** StreamingContinueSessionRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| userInput | objectType | True | The user message for the Agent to respond to. |
| parameterInputs | mapType | False | Any supplied values for [application variables](/docs/foundry/chatbot-studio/application-state/) to pass to the Agent for the exchange. |
| contextsOverride | listType | False | If set, automatic [context](/docs/foundry/chatbot-studio/retrieval-context/) retrieval is skipped and the list of specified context is provided to the Agent instead. If omitted, relevant context for the user message is automatically retrieved and included in the prompt, based on data sources configured on the Agent for the session. |
| messageId | stringType | False | A client-generated Universally Unique Identifier (UUID) to identify the message, which the client can use to cancel the exchange before the streaming response is complete. |
| sessionTraceId | stringType | False | The unique identifier to use for this continue session trace. By generating and passing this ID to the `streamingContinue` endpoint, clients can use this trace ID to separately load details of the trace used to generate a result, while the result is in progress. If omitted, it will be generated automatically. Clients can check the generated ID by inspecting the `sessionTraceId` in the `SessionExchangeResult`, which can be loaded via the `getContent` endpoint. |

**example:** {"sessionTraceId":"12345678-1234-5678-1234-123456789abc","messageId":"00f8412a-c29d-4063-a417-8052825285a5","userInput":{"text":"What is the status of my order?"},"parameterInputs":{"currentCustomerOrders":{"type":"objectSet","ontology":"example-ontology","objectSet":{"type":"filter","objectSet":{"type":"base","objectType":"customerOrder"},"where":{"type":"eq","field":"customerId","value":"123abc"}}}}}

### Response

#### Body

**name:** body

##### Format

### Error Responses

| name | description |
| --- | --- |
| ObjectTypeIdsNotFound | Some object types are configured for use by the Agent but could not be found. The object types either do not exist or the client token does not have access. Object types can be checked by listing available object types through the API, or searching in [Ontology Manager](/docs/foundry/ontology-manager/overview/). |
| ObjectTypeRidsNotFound | Some object types are configured for use by the Agent but could not be found. The object types either do not exist or the client token does not have access. Object types can be checked by listing available object types through the API, or searching in [Ontology Manager](/docs/foundry/ontology-manager/overview/). |
| FunctionLocatorNotFound | The specified function locator is configured for use by the Agent but could not be found. The function type or version may not exist or the client token does not have access. |
| InvalidParameter | The provided application variable is not valid for the Agent for this session. Check the available application variables for the Agent under the `parameters` property, and version through the API with `getAgent`, or in AIP Chatbot Studio. The Agent version used for the session can be checked through the API with `getSession`. |
| InvalidParameterType | The provided value does not match the expected type for the application variable configured on the Agent for this session. Check the available application variables for the Agent under the `parameters` property, and version through the API with `getAgent`, or in AIP Chatbot Studio. The Agent version used for the session can be checked through the API with `getSession`. |
| SessionTraceIdAlreadyExists | The provided trace ID already exists for the session and cannot be reused. |
| OntologyEntitiesNotFound | Some ontology types are configured for use by the Agent but could not be found. The types either do not exist or the client token does not have access. Object types and their link types can be checked by listing available object/link types through the API, or searching in [Ontology Manager](/docs/foundry/ontology-manager/overview/). |
| StreamingContinueSessionPermissionDenied | Could not streamingContinue the Session. |
| SessionNotFound | The given Session could not be found. |
| AgentNotFound | The given Agent could not be found. |
