---
source_url: "https://www.palantir.com/docs/foundry/api/v2/sql-queries-v2-resources/sql-queries/execute-sql-query/"
parquet_url: "/foundry/api/v2/sql-queries-v2-resources/sql-queries/execute-sql-query/"
title: "Execute Sql Query"
fetched_at: "2026-05-12T19:34:37.592Z"
---
Execute Sql Query. Executes a new query. Only the user that invoked the query can operate on the query. The size of query results are limited by default to 1 million rows. Contact your Palantir representative to discuss limit increases. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:sql-queries-execute. Request body. The SQL query to execute. Queries should conform to the Spark SQL dialect. This supports SELECT queries only. Datasets can be referenced in SQL queries by path or by RID. See the documentation for more details. The list of branch ids to use as fallbacks if the query fails to execute on the primary branch. If a is not explicitly provided in the SQL query, the resource will be queried on the first fallback branch provided that exists. If no fallback branches are provided the default branch is used. This is master for most enrollments. The format used to serialize query results. If not specified, defaults to ARROW. Enum values: ARROW, CSV. Response body. Examples. Error responses.
