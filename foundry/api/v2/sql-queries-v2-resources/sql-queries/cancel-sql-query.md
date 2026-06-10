---
source_url: "https://www.palantir.com/docs/foundry/api/v2/sql-queries-v2-resources/sql-queries/cancel-sql-query/"
title: "Cancel Sql Query"
---
# Cancel Sql Query

Cancels a query. If the query is no longer running this is effectively a no-op. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:sql-queries-execute. Path parameters. The unique identifier for a query. Note that query IDs are not URL-safe and must be URL-encoded when used in API endpoints. Examples. Error responses.
