---
source_url: "https://www.palantir.com/docs/foundry/api/v2/aip-agents-v2-resources/sessions/get-session/"
parquet_url: "/foundry/api/v2/aip-agents-v2-resources/sessions/get-session/"
title: "Get Session"
fetched_at: "2026-05-12T19:34:37.570Z"
---
Get Session. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Get the details of a conversation session between the calling user and an Agent. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:aip-agents-read. Path parameters. An RID identifying an Agent created in AIP Chatbot Studio. The Resource Identifier (RID) of the conversation session. Query parameters. Enables the use of preview functionality. Response body. The Resource Identifier (RID) of the conversation session. Metadata about the session. The Resource Identifier (RID) of the Agent associated with the session. The version of the Agent associated with the session. This can be set by clients on session creation. If not specified, defaults to use the latest published version of the Agent at session creation time. Examples. Error responses.
