---
source_url: "https://www.palantir.com/docs/gotham/api/inbox-resources/messages/inbox-send-messages/"
title: "Send Inbox Messages \u2022 API Reference"
---
# Send Inbox Messages

## Endpoint

:::callout{theme=warning title=Warning}
This endpoint is in preview and may be modified or removed at any time.
To use this endpoint, add `preview=true` to the request query parameters.
:::

Send messages in Global Inbox.

Validation failure for any message will cause the entire request to throw before any messages are sent.

The response reports all messages which were successfully sent, and any messages which failed to
be sent due to a conflict with an existing message.

Callers must be added to the internal "External Inbox Alert Producers" group in Gotham Security (multipass).

Note that the recipient `realm` must be specified if the caller's `realm` is not identical. For
example, to send to the "Everyone" group in the "palantir-internal-realm" realm, the caller must either specify the realm or already be
in "palantir-internal-realm".

**operationId:** v1.sendMessages

**path:** /api/gotham/v1/inbox/messages

### Operation Type

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Represents a boolean value that restricts an endpoint to preview mode when set to true. |

### Request

#### Body

**name:** SendMessagesRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| messages | listType | False |  |

**example:** {"messages":[{"sender":{"displayName":"My External Message Sender"},"title":{"value":"Hello from the sendMessages API!"},"security":{"portionMarkings":["SENSITIVE"]},"groupRecipients":[{"name":"my-example-group"}],"body":{"value":"Some **styled** extra content for my message","formatStyle":"MARKDOWN"}}]}

### Response

#### Body

Success response

**name:** SendMessagesResponse

**example:** {"responses":[{"sourceId":"f81d4fae-7dec-11d0-a765-00a0c91e6bf6"}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| responses | listType | False | The list of messages which were sent successfully. Messages are returned in the order in which they were sent in the request. |
| failures | listType | False | The list of messages which failed to be sent in Inbox due to conflicts with existing messages. |

**example:** {"responses":[{"sourceId":"f81d4fae-7dec-11d0-a765-00a0c91e6bf6"}]}
