---
source_url: "https://www.palantir.com/docs/foundry/api/v2/aip-agents-v2-resources/sessions/create-session/"
title: "Create Session"
---
# Create Session

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Create a new conversation session between the calling user and an Agent. Use blockingContinue or streamingContinue to start adding exchanges to the session. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:aip-agents-write. Path parameters. An RID identifying an Agent created in AIP Chatbot Studio. Query parameters. Enables the use of preview functionality. Request body. The version of the Agent associated with the session. This can be set by clients on session creation. If not specified, defaults to use the latest published version of the Agent at session creation time. Response body. The created Session. The Resource Identifier (RID) of the conversation session. Metadata about the session. The Resource Identifier (RID) of the Agent associated with the session. The version of the Agent associated with the session. This can be set by clients on session creation. If not specified, defaults to use the latest published version of the Agent at session creation time. Examples. Error responses.
