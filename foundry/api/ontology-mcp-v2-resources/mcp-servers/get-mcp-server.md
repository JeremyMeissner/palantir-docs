---
source_url: "https://www.palantir.com/docs/foundry/api/ontology-mcp-v2-resources/mcp-servers/get-mcp-server/"
title: "Get Mcp Server \u2022 API Reference"
---
# Get Mcp Server

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Get details of an MCP server.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:ontology-mcp-read`.

**operationId:** v2.getMcpServer

**path:** /api/v2/ontologyMcp/mcpServers/{mcpServerRid}

### Operation Type

### Scopes

| name |
| --- |
| api:ontology-mcp-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| mcpServerRid | stringType | True | The RID of the MCP server. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** McpServer

**example:** {"name":"My MCP Server","description":"An MCP server that provides access to custom tools.","rid":"ri.third-party-applications.main.application.a1b2c3d4-e5f6-7890-abcd-ef1234567890"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| rid | stringType | True | The RID of the MCP server. |
| name | stringType | True | The display name of the MCP server. |
| description | stringType | True | An LLM-oriented description of the MCP server. |

**example:** {"name":"My MCP Server","description":"An MCP server that provides access to custom tools.","rid":"ri.third-party-applications.main.application.a1b2c3d4-e5f6-7890-abcd-ef1234567890"}

### Error Responses

| name | description |
| --- | --- |
| McpServerNotFound | The given McpServer could not be found. |
