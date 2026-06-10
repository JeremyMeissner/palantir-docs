---
source_url: "https://www.palantir.com/docs/foundry/api/sql-queries-v2-resources/sql-queries/get-status-sql-query/"
title: "Get Status Sql Query \u2022 API Reference"
---
# Get Status Sql Query

## Endpoint

Gets the status of a query.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:sql-queries-read`.

**operationId:** v2.getStatusSqlQuery

**path:** /api/v2/sqlQueries/{sqlQueryId}/getStatus

### Operation Type

### Scopes

| name |
| --- |
| api:sql-queries-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| sqlQueryId | stringType | True | The unique identifier for a query. Note that query IDs are not URL-safe and must be URL-encoded when used in API endpoints. |

### Response

#### Body

**name:** QueryStatus

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| running | objectType | False |  |
| canceled | objectType | False |  |
| failed | objectType | False |  |
| succeeded | objectType | False |  |

### Error Responses

| name | description |
| --- | --- |
| QueryPermissionDenied | The provided token does not have permission to access the given query. |
| QueryCanceled | The query was canceled. |
| QueryFailed | The query failed. |
| QueryParseError | The query cannot be parsed. |
| QueryRunning | The query is running. |
| ReadQueryInputsPermissionDenied | The provided token does not have permission to access the inputs to the query. |
| GetStatusSqlQueryPermissionDenied | Could not getStatus the SqlQuery. |
