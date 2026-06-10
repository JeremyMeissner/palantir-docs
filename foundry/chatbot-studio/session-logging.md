---
source_url: "https://www.palantir.com/docs/foundry/chatbot-studio/session-logging/"
title: "Documentation | AIP Chatbot Studio > Session logging"
---
# Session logging

Chatbot executions in AIP Chatbot Studio are logged as structured events that can be exported to a Foundry streaming dataset for monitoring and analysis. Each message sent to a chatbot counts as one execution, and every execution is assigned a unique trace identifier that connects all related log entries.

:::callout{theme="neutral"}
Chatbot session log exporting uses the [configure logging](/docs/foundry/administration/configure-logging/) feature. Event schemas and event types are subject to change. New events may be added and existing schemas may be modified.
:::

## Prerequisites

Exporting chatbot session logs requires the log export feature. See [export permissions](/docs/foundry/administration/configure-logging/#export-permissions) for the required roles. Chatbot execution logs contain user identifiers that can be traced back to the user who sent the message, so access to exported log data should be carefully managed.

To set up log exporting, follow the steps in the [Configure logging](/docs/foundry/administration/configure-logging/) documentation, including the recommended **Apply markings** step to apply [security markings](/docs/foundry/security/markings/) to the output streaming dataset to control access to log data.

[Learn how to view logs in the platform with AIP observability.](/docs/foundry/aip-observability/overview/)

## Understanding chatbot execution logs

Each log entry contains common fields provided by the [log schema](/docs/foundry/administration/configure-logging/#log-schema), as well as chatbot-specific event data. The chatbot-specific data consists of an `event_name` and a `payload` describing what occurred during the execution.

### Common log fields

The following fields are included in every log entry and are useful for filtering and correlating logs. Logs from products across the execution flow, such as function executions and language model usage, also share these fields, so you can use them to trace the complete execution request:

| Field | Type | Description |
|---|---|---|
| `traceId` | String | A Foundry trace identifier assigned to each execution. All log entries from the same execution share the same `traceId`. Use this to follow a request end-to-end. |
| `uid` | String | The identifier of the user who sent the message. |
| `owning_rid` | String | The resource identifier of the source executor that initiated the execution, such as a chatbot, function, or Workshop application. For example, if Chatbot A calls a function that invokes Chatbot B, all resulting logs have Chatbot A's RID as the `owning_rid`. Use this to find all logs originating from a specific source executor, regardless of how deep the call chain goes. |

### Chatbot event data

Each chatbot event includes an `event_name` identifying the type of event and a `payload` with event-specific fields. Every event payload includes a `session_rid`, which identifies the chatbot session. Use this to group all events from a single conversation.

### Sample log structure

The following is a simplified example of a log entry for a `user_request` event:

```json
{
  "time": "2024-01-15T09:30:00.000Z",
  "uid": "<USER_ID>",
  "traceId": "<TRACE_ID>",
  "content": {
    "event_name": "user_request",
    "payload": {
      "session_rid": "ri.aip-agents..session.<SESSION_ID>",
      "user_query": {
        "content": [
          {
            "text": {
              "content": "Summarize the key points from the latest press conference transcript."
            }
          }
        ]
      }
    }
  }
}
```

## Event types

The following event types are logged during a chatbot execution:

| Event name | Description |
|---|---|
| `session_metadata` | Records the chatbot RID, chatbot version, session RID, and caller identifier at the start of an execution. |
| `user_request` | Captures the user's message along with any retrieval context and application variables. |
| `system_chat_message` | Contains the compiled system prompt sent to the LLM, including tool definitions. |
| `user_chat_message` | Contains the user message content as sent to the LLM. |
| `assistant_chat_message` | Contains the LLM's response content, which may include text or tool calls. |
| `tool_call` | Records a tool invocation, including the tool name and parsed input. |
| `tool_call_result` | Records the result of a tool invocation, including whether it succeeded or failed, and how long it took. |
| `final_response` | Contains the chatbot's final response returned to the user. |
| `execution_error` | Records an error that occurred during execution. |

### Session metadata

Logged once at the start of each execution with identifying information about the chatbot and session.

| Field | Type | Description |
|---|---|---|
| `agent_rid` | String | The resource identifier of the chatbot. |
| `agent_version` | String | The version of the chatbot. |
| `session_rid` | String | The resource identifier of the session. |
| `caller_identifier` | String | An identifier for the caller that initiated the execution. |

### User request

Captures the full context of a user's message, including any retrieval context and application variables that were resolved for this execution.

| Field | Type | Description |
|---|---|---|
| `session_rid` | String | The session identifier. |
| `user_query` | UserQuery | The user's message content, which may include text and media. |
| `contexts_from_profile` | List\<Context> | Retrieval contexts resolved from the chatbot's configured context sources. Each context represents a specific context type, such as Ontology, document, function-backed, or custom documentation. |
| `contexts_from_user_input` | List\<Context> | Retrieval contexts resolved from the user's input. |
| `application_variables` | List\<ApplicationVariable> | The application variables and their values at the time of the request. Each variable includes its identifier, name, value, and prompt visibility setting. |
| `node_id` | String | An identifier for the execution node. |
| `parent_node_id` | String (optional) | The identifier for the session node this execution was continued from. |

### Chat messages

The `system_chat_message`, `user_chat_message`, and `assistant_chat_message` events share a similar structure.

| Field | Type | Description |
|---|---|---|
| `session_rid` | String | The session identifier. |
| `content` | List\<Content> | The message content, which may include text, media references, or tool calls. |
| `native_tools` | List\<NativeTool> | The tools available to the LLM when using [native tool calling](/docs/foundry/chatbot-studio/tools/#tool-mode) mode. Only present in `system_chat_message`. Tools configured in prompted tool calling mode are included in the `content` field instead. |

### Tool calls

The `tool_call` event records when the chatbot invokes a tool.

| Field | Type | Description |
|---|---|---|
| `session_rid` | String | The session identifier. |
| `tool_name` | String | The name of the tool that was called. |
| `parsed_tool_input` | Map\<String, String> | A map of input parameter names to their values. |

### Tool call results

The `tool_call_result` event records the outcome of a tool invocation.

| Field | Type | Description |
|---|---|---|
| `session_rid` | String | The session identifier. |
| `tool_name` | String | The name of the tool that was called. |
| `tool_call_id` | String (optional) | An identifier for the specific tool call. |
| `duration_milliseconds` | Long | How long the tool call took to execute, in milliseconds. |
| `result` | ToolResult | The result of the tool call, which is one of the following: |

The `ToolResult` type is one of:

* **Success:** Contains an `llm_value` (String) with the value returned to the LLM, and a `variable_updates` list with the variable name and new value for any application variables that were updated.
* **Failure:** Contains an `error_message` (String) and a `reason` (String) describing why the tool call failed.

### Final response

Contains the chatbot's final response to the user.

| Field | Type | Description |
|---|---|---|
| `session_rid` | String | The session identifier. |
| `response` | FinalResponse | The response content, which is one of the following: |

The `FinalResponse` type is one of:

* **Chatbot response:** Contains a list of content items, which may include text and media.
* **Client tool call:** Indicates the chatbot is deferring to a client-side action rather than returning a direct response.

### Execution errors

Logged when an error occurs during execution.

| Field | Type | Description |
|---|---|---|
| `session_rid` | String | The session identifier. |
| `error_name` | String | The name or type of the error. |

## Examples

### Reconstruct a conversation

To reconstruct a chat conversation with a specific chatbot:

1. Filter logs where `owning_rid` matches the chatbot's RID.
2. Filter further by `session_rid` to isolate a single conversation.
3. For user messages, find entries where `event_name` is `user_request` and extract `user_query` from the payload.
4. For chatbot replies, find entries where `event_name` is `final_response` and extract `response` from the payload.

### Evaluate tool performance

To analyze how tools are performing:

1. Find entries where `event_name` is `tool_call_result`. Each entry includes the `tool_name`, `duration_milliseconds`, and whether the call succeeded or failed.
2. To measure reliability, compare the count of success results versus failure results per tool.
3. To identify slow tools, sort by `duration_milliseconds`.
4. To detect retries, look for multiple `tool_call` and `tool_call_result` pairs with the same `tool_name` within a single `traceId`. A failure followed by another call to the same tool indicates the chatbot retried.
