---
source_url: "https://www.palantir.com/docs/foundry/api/v2/sql-queries-v2-resources/sql-queries/get-results-sql-query/"
title: "Get Results Sql Query"
---
# Get Results Sql Query

Gets the results of a query. Results are returned in the serializationFormat specified at execute time (defaulting to Apache Arrow if no format is provided). This endpoint implements long polling and requests will time out after one minute. They can be safely retried while the query is still running. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:sql-queries-read. Path parameters. The unique identifier for a query. Note that query IDs are not URL-safe and must be URL-encoded when used in API endpoints. Response body. Examples. Error responses.
