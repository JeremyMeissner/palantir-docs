---
source_url: "https://www.palantir.com/docs/foundry/api/aip-agents-v2-resources/agents/list-sessions-for-agents/"
title: "List Sessions For Agents \u2022 API Reference"
---
# List Sessions For Agents

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

List all conversation sessions between the calling user and all accessible Agents that were created by this client.
Sessions are returned in order of most recently updated first.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:aip-agents-write`.

**operationId:** v2.listSessionsForAgents

**path:** /api/v2/aipAgents/agents/allSessions

### Operation Type

### Scopes

| name |
| --- |
| api:aip-agents-write |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| pageSize | integerType | False | The maximum number of sessions to return in a single page. The maximum allowed value is 100. Defaults to 100 if not specified. |
| pageToken | stringType | False | The page token indicates where to start paging. This should be omitted from the first page's request. To fetch the next page, clients should take the value from the `nextPageToken` field of the previous response and use it to populate the `pageToken` field of the next request. |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

A page of results for sessions across all accessible Agents for the calling user.
Sessions are returned in order of most recently updated first.

**name:** AgentsSessionsPage

**example:** {"data":[{"metadata":{"updatedTime":"2024-10-01T22:04:24.962583055Z","estimatedExpiresTime":"2024-10-02T22:04:24.962583055Z","messageCount":6,"createdTime":"2024-10-01T20:04:24.962583055Z","title":"What is the status of my order?"},"agentRid":"ri.aip-agents..agent.732cd5b4-7ca7-4219-aabb-6e976faf63b1","agentVersion":"1.0","rid":"ri.aip-agents..session.292db3b2-b653-4de6-971c-7e97a7b881d6"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| nextPageToken | stringType | False | The page token that should be used when requesting the next page of results. Empty if there are no more results to retrieve. |
| data | listType | False |  |

**example:** {"data":[{"metadata":{"updatedTime":"2024-10-01T22:04:24.962583055Z","estimatedExpiresTime":"2024-10-02T22:04:24.962583055Z","messageCount":6,"createdTime":"2024-10-01T20:04:24.962583055Z","title":"What is the status of my order?"},"agentRid":"ri.aip-agents..agent.732cd5b4-7ca7-4219-aabb-6e976faf63b1","agentVersion":"1.0","rid":"ri.aip-agents..session.292db3b2-b653-4de6-971c-7e97a7b881d6"}],"nextPageToken":"v1.QnVpbGQgdGhlIEZ1dHVyZTogaHR0cHM6Ly93d3cucGFsYW50aXIuY29tL2NhcmVlcnMvP2xldmVyLXNvdXJjZSU1YiU1ZD1BUElEb2NzI29wZW4tcG9zaXRpb25z"}

### Error Responses

| name | description |
| --- | --- |
| GetAllSessionsAgentsPermissionDenied | The calling user does not have permission to list all sessions across all Agents. Listing all sessions across all agents requires the `api:aip-agents-write` scope. |
| ListSessionsForAgentsPermissionDenied | Could not allSessions the Agent. |
