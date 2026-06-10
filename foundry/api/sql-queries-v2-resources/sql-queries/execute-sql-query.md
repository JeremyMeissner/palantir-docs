---
source_url: "https://www.palantir.com/docs/foundry/api/sql-queries-v2-resources/sql-queries/execute-sql-query/"
title: "Execute Sql Query \u2022 API Reference"
---
# Execute Sql Query

## Endpoint

Executes a new query. Only the user that invoked the query can operate on the query. The size of query
results are limited by default to 1 million rows. Contact your Palantir representative to discuss limit
increases.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:sql-queries-execute`.

**operationId:** v2.executeSqlQuery

**path:** /api/v2/sqlQueries/execute

### Operation Type

### Scopes

| name |
| --- |
| api:sql-queries-execute |

### Request

#### Body

**name:** ExecuteSqlQueryRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| query | stringType | True | The SQL query to execute. Queries should conform to the [Spark SQL dialect](https://spark.apache.org/docs/latest/sql-ref.html). This supports SELECT queries only. Datasets can be referenced in SQL queries by path or by RID. See the  [documentation](https://www.palantir.com/docs/foundry/analytics-connectivity/odbc-jdbc-drivers/#use-sql-to-query-foundry-datasets) for more details. |
| fallbackBranchIds | listType | False | The list of branch ids to use as fallbacks if the query fails to execute on the primary branch. If a is not explicitly provided in the SQL query, the resource will be queried on the first fallback branch provided that exists. If no fallback branches are provided the default branch is used. This is `master` for most enrollments. |
| serializationFormat | enumType | False | The format used to serialize query results. If not specified, defaults to `ARROW`. |

**example:** {"fallbackBranchIds":["master"],"serializationFormat":"CSV","query":"SELECT * FROM `/Path/To/Dataset`"}

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
| ColumnTypesNotSupported | The query result contains column types that are not supported by the requested serialization format. |
| ReadQueryInputsPermissionDenied | The provided token does not have permission to access the inputs to the query. |
| QueryParseError | The query cannot be parsed. |
| QueryCanceled | The query was canceled. |
| QueryPermissionDenied | The provided token does not have permission to access the given query. |
| QueryFailed | The query failed. |
| QueryRunning | The query is running. |
| ExecuteSqlQueryPermissionDenied | Could not execute the SqlQuery. |
