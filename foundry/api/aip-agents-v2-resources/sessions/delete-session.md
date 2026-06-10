---
source_url: "https://www.palantir.com/docs/foundry/api/aip-agents-v2-resources/sessions/delete-session/"
title: "Delete Session \u2022 API Reference"
---
# Delete Session

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Delete a conversation session between the calling user and an Agent.
Once deleted, the session can no longer be accessed and will not appear in session lists.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:aip-agents-write`.

**operationId:** v2.deleteSession

**path:** /api/v2/aipAgents/agents/{agentRid}/sessions/{sessionRid}

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

### Error Responses

| name | description |
| --- | --- |
| DeleteSessionPermissionDenied | Could not delete the Session. |
| SessionNotFound | The given Session could not be found. |
| AgentNotFound | The given Agent could not be found. |
