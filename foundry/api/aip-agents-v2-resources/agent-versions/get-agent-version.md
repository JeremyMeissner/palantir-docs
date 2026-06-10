---
source_url: "https://www.palantir.com/docs/foundry/api/aip-agents-v2-resources/agent-versions/get-agent-version/"
title: "Get Agent Version \u2022 API Reference"
---
# Get Agent Version

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Get version details for an Agent.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:aip-agents-read`.

**operationId:** v2.getAgentVersion

**path:** /api/v2/aipAgents/agents/{agentRid}/agentVersions/{agentVersionString}

### Operation Type

### Scopes

| name |
| --- |
| api:aip-agents-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| agentRid | stringType | True | An RID identifying an Agent created in [AIP Chatbot Studio](/docs/foundry/chatbot-studio/overview/). |
| agentVersionString | stringType | True | The semantic version of the Agent, formatted as "majorVersion.minorVersion". |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Response

#### Body

**name:** AgentVersion

**example:** {"string":"1.0","version":{"major":1,"minor":2}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| string | stringType | True | The semantic version of the Agent, formatted as "majorVersion.minorVersion". |
| version | objectType | True | Semantic version details of the Agent. |

**example:** {"string":"1.0","version":{"major":1,"minor":2}}

### Error Responses

| name | description |
| --- | --- |
| InvalidAgentVersion | The provided version string is not a valid format for an Agent version. |
| NoPublishedAgentVersion | Failed to retrieve the latest published version of the Agent because the Agent has no published versions. Try publishing the Agent in AIP Chatbot Studio to use the latest published version, or specify the version of the Agent to use. |
| AgentVersionNotFound | The given AgentVersion could not be found. |
| AgentNotFound | The given Agent could not be found. |
