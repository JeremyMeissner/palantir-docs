---
source_url: "https://www.palantir.com/docs/foundry/api/aip-agents-v2-resources/sessions/list-sessions/"
title: "List Sessions \u2022 API Reference"
---
# List Sessions

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

List all conversation sessions between the calling user and an Agent that was created by this client.
This does not list sessions for the user created by other clients.
For example, any sessions created by the user in AIP Chatbot Studio will not be listed here.
Sessions are returned in order of most recently updated first.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:aip-agents-read`.

**operationId:** v2.listSessions

**path:** /api/v2/aipAgents/agents/{agentRid}/sessions

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
| pageSize | integerType | False | The page size to use for the endpoint. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** ListSessionsResponse

**example:** {"data":[{"metadata":{"updatedTime":"2024-10-01T22:04:24.962583055Z","estimatedExpiresTime":"2024-10-02T22:04:24.962583055Z","messageCount":6,"createdTime":"2024-10-01T20:04:24.962583055Z","title":"What is the status of my order?"},"agentRid":"ri.aip-agents..agent.732cd5b4-7ca7-4219-aabb-6e976faf63b1","agentVersion":"1.0","rid":"ri.aip-agents..session.292db3b2-b653-4de6-971c-7e97a7b881d6"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | listType | False |  |
| nextPageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |

**example:** {"data":[{"metadata":{"updatedTime":"2024-10-01T22:04:24.962583055Z","estimatedExpiresTime":"2024-10-02T22:04:24.962583055Z","messageCount":6,"createdTime":"2024-10-01T20:04:24.962583055Z","title":"What is the status of my order?"},"agentRid":"ri.aip-agents..agent.732cd5b4-7ca7-4219-aabb-6e976faf63b1","agentVersion":"1.0","rid":"ri.aip-agents..session.292db3b2-b653-4de6-971c-7e97a7b881d6"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| AgentNotFound | The given Agent could not be found. |
