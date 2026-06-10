---
source_url: "https://www.palantir.com/docs/foundry/api/aip-agents-v2-resources/session-traces/get-session-trace/"
title: "Get Session Trace \u2022 API Reference"
---
# Get Session Trace

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Get the trace of an Agent response. The trace lists the sequence of steps that an Agent took to arrive at
an answer. For example, a trace may include steps such as context retrieval and tool calls. Clients should
poll this endpoint to check the realtime progress of a response until the trace is completed.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:aip-agents-read`.

**operationId:** v2.getSessionTrace

**path:** /api/v2/aipAgents/agents/{agentRid}/sessions/{sessionRid}/sessionTraces/{sessionTraceId}

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
| sessionTraceId | stringType | True | The unique identifier for the trace. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** SessionTrace

**example:** {"toolCallGroups":[{"toolCalls":[{"toolMetadata":{"name":"Object Query Tool","type":"FUNCTION"},"input":{"thought":"I need to find the customer with the name 'Titan Technologies'."}}]}],"id":"12345678-1234-5678-1234-123456789abc","contexts":{"objectContexts":[{"objectRids":["ri.phonograph2-objects.main.object.48668bf6-8878-48d2-b8f8-f0017593feb5"],"propertyTypeRids":["ri.ontology.main.property.7899aeb4-a389-4f2e-a0fd-e7193a4f6cb1"]}]},"status":"IN_PROGRESS"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| id | stringType | True | The unique identifier for the trace. |
| status | enumType | True | This indicates whether the Agent has finished generating the final response. Clients should keep polling the `getSessionTrace` endpoint until the status is `COMPLETE`. |
| contexts | objectType | False | Any additional context which was provided by the client or retrieved automatically by the agent, grouped by context type. Empty if no additional context was provided or configured to be automatically retrieved. A present SessionExchangeContexts object with empty lists indicates that context retrieval was attempted but no context was found. Note that this field will only be populated once the response generation has completed. |
| toolCallGroups | listType | False | List of tool call groups that were triggered at the same point in the trace for the agent response generation. The groups are returned in the same order as they were triggered by the agent. |

**example:** {"toolCallGroups":[{"toolCalls":[{"toolMetadata":{"name":"Object Query Tool","type":"FUNCTION"},"input":{"thought":"I need to find the customer with the name 'Titan Technologies'."}}]}],"id":"12345678-1234-5678-1234-123456789abc","contexts":{"objectContexts":[{"objectRids":["ri.phonograph2-objects.main.object.48668bf6-8878-48d2-b8f8-f0017593feb5"],"propertyTypeRids":["ri.ontology.main.property.7899aeb4-a389-4f2e-a0fd-e7193a4f6cb1"]}]},"status":"IN_PROGRESS"}

### Error Responses

| name | description |
| --- | --- |
| SessionTraceNotFound | The given SessionTrace could not be found. |
| SessionNotFound | The given Session could not be found. |
| AgentNotFound | The given Agent could not be found. |
