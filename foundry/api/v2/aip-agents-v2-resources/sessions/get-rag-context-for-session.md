---
source_url: "https://www.palantir.com/docs/foundry/api/v2/aip-agents-v2-resources/sessions/get-rag-context-for-session/"
title: "Get Rag Context For Session"
---
# Get Rag Context For Session

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Retrieve relevant context for a user message from the data sources configured for the session. This allows clients to pre-retrieve context for a user message before sending it to the Agent with the contextsOverride option when continuing a session, to allow any pre-processing of the context before sending it to the Agent. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:aip-agents-write. Path parameters. An RID identifying an Agent created in AIP Chatbot Studio. The Resource Identifier (RID) of the conversation session. Query parameters. Enables the use of preview functionality. Request body. The user message to retrieve relevant context for from the configured Agent data sources. Any values for application variables to use for the context retrieval. Response body. Context retrieved from an Agent's configured context data sources which was relevant to the supplied user message. Examples. Error responses.
