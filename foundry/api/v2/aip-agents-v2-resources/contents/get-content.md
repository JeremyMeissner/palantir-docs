---
source_url: "https://www.palantir.com/docs/foundry/api/v2/aip-agents-v2-resources/contents/get-content/"
title: "Get Content"
---
# Get Content

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Get the conversation content for a session between the calling user and an Agent. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:aip-agents-read. Path parameters. An RID identifying an Agent created in AIP Chatbot Studio. The Resource Identifier (RID) of the conversation session. Query parameters. Enables the use of preview functionality. Response body. The conversation history for the session, represented as a list of exchanges. Each exchange represents an initiating message from the user and the Agent's response. Exchanges are returned in chronological order, starting with the first exchange. Examples. Error responses.
