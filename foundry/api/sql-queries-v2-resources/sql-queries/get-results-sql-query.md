---
source_url: "https://www.palantir.com/docs/foundry/api/sql-queries-v2-resources/sql-queries/get-results-sql-query/"
title: "Get Results Sql Query \u2022 API Reference"
---
# Get Results Sql Query

## Endpoint

Gets the results of a query. Results are returned in the `serializationFormat` specified at execute time
(defaulting to [Apache Arrow](https://arrow.apache.org/) if no format is provided).

This endpoint implements long polling and requests will time out after one minute. They can be safely
retried while the query is still running.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:sql-queries-read`.

**operationId:** v2.getResultsSqlQuery

**path:** /api/v2/sqlQueries/{sqlQueryId}/getResults

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

**name:** body

##### Format

### Error Responses

| name | description |
| --- | --- |
| QueryCanceled | The query was canceled. |
| QueryFailed | The query failed. |
| QueryParseError | The query cannot be parsed. |
| QueryRunning | The query is running. |
| ReadQueryInputsPermissionDenied | The provided token does not have permission to access the inputs to the query. |
| QueryPermissionDenied | The provided token does not have permission to access the given query. |
| GetResultsSqlQueryPermissionDenied | Could not getResults the SqlQuery. |
