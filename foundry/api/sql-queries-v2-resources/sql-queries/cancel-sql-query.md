---
source_url: "https://www.palantir.com/docs/foundry/api/sql-queries-v2-resources/sql-queries/cancel-sql-query/"
title: "Cancel Sql Query \u2022 API Reference"
---
# Cancel Sql Query

## Endpoint

Cancels a query. If the query is no longer running this is effectively a no-op.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:sql-queries-execute`.

**operationId:** v2.cancelSqlQuery

**path:** /api/v2/sqlQueries/{sqlQueryId}/cancel

### Operation Type

### Scopes

| name |
| --- |
| api:sql-queries-execute |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| sqlQueryId | stringType | True | The unique identifier for a query. Note that query IDs are not URL-safe and must be URL-encoded when used in API endpoints. |

### Error Responses

| name | description |
| --- | --- |
| QueryPermissionDenied | The provided token does not have permission to access the given query. |
| QueryCanceled | The query was canceled. |
| QueryFailed | The query failed. |
| QueryParseError | The query cannot be parsed. |
| QueryRunning | The query is running. |
| ReadQueryInputsPermissionDenied | The provided token does not have permission to access the inputs to the query. |
| CancelSqlQueryPermissionDenied | Could not cancel the SqlQuery. |
