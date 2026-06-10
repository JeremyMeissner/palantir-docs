---
source_url: "https://www.palantir.com/docs/foundry/api/aip-agents-v2-resources/sessions/update-session-title/"
title: "Update Session Title \u2022 API Reference"
---
# Update Session Title

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Update the title for a session.
Use this to set a custom title for a session to help identify it in the list of sessions with an Agent.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:aip-agents-write`.

**operationId:** v2.updateSessionTitle

**path:** /api/v2/aipAgents/agents/{agentRid}/sessions/{sessionRid}/updateTitle

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

**name:** UpdateSessionTitleRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| title | stringType | True | The new title for the session. The maximum title length is 200 characters. Titles are truncated if they exceed this length. |

**example:** {"title":"Order status 02/01"}

### Error Responses

| name | description |
| --- | --- |
| UpdateSessionTitlePermissionDenied | Could not updateTitle the Session. |
| SessionNotFound | The given Session could not be found. |
| AgentNotFound | The given Agent could not be found. |
