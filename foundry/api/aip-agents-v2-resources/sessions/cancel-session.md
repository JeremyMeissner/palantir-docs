---
source_url: "https://www.palantir.com/docs/foundry/api/aip-agents-v2-resources/sessions/cancel-session/"
title: "Cancel Session \u2022 API Reference"
---
# Cancel Session

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Cancel an in-progress streamed exchange with an Agent which was initiated with `streamingContinue`.
Canceling an exchange allows clients to prevent the exchange from being added to the session, or to provide a response to replace the Agent-generated response.
Note that canceling an exchange does not terminate the stream returned by `streamingContinue`; clients should close the stream on triggering the cancellation request to stop reading from the stream.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:aip-agents-write`.

**operationId:** v2.cancelSession

**path:** /api/v2/aipAgents/agents/{agentRid}/sessions/{sessionRid}/cancel

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

**name:** CancelSessionRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| messageId | stringType | True | The identifier for the in-progress exchange to cancel. This should match the `messageId` which was provided when initiating the exchange with `streamingContinue`. |
| response | stringType | False | When specified, the exchange is added to the session with the client-provided response as the result. When omitted, the exchange is not added to the session. |

**example:** {"response":"The status of your order is **In Transit**.","messageId":"00f8412a-c29d-4063-a417-8052825285a5"}

### Response

#### Body

**name:** CancelSessionResponse

**example:** {"result":{"totalTokensUsed":6448,"agentMarkdownResponse":"The status of your order is **In Transit**.","sessionTraceId":"12345678-1234-5678-1234-123456789abc","interruptedOutput":false}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| result | objectType | False | If the `response` field was specified, this returns the result that was added to the session for the canceled exchange, with the client-provided response. If no `response` was specified in the request, this returns an empty response, as no exchange was added to the session. |

**example:** {"result":{"totalTokensUsed":6448,"agentMarkdownResponse":"The status of your order is **In Transit**.","sessionTraceId":"12345678-1234-5678-1234-123456789abc","interruptedOutput":false}}

### Error Responses

| name | description |
| --- | --- |
| CancelSessionFailedMessageNotInProgress | Unable to cancel the requested session exchange as no in-progress exchange was found for the provided message identifier. This is expected if no exchange was initiated with the provided message identifier through a `streamingContinue` request, or if the exchange for this identifier has already completed and cannot be canceled, or if the exchange has already been canceled. This error can also occur if the cancellation was requested immediately after requesting the exchange through a `streamingContinue` request, and the exchange has not started yet. Clients should handle these errors gracefully, and can reload the session content to get the latest conversation state. |
| CancelSessionPermissionDenied | Could not cancel the Session. |
| SessionNotFound | The given Session could not be found. |
| AgentNotFound | The given Agent could not be found. |
