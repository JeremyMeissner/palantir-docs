---
source_url: "https://www.palantir.com/docs/foundry/api/v2/datasets-v2-resources/transactions/get-transaction/"
parquet_url: "/foundry/api/v2/datasets-v2-resources/transactions/get-transaction/"
title: "Get Transaction"
fetched_at: "2026-05-12T19:34:37.553Z"
---
Get Transaction. Gets a Transaction of a Dataset. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:datasets-read. Path parameters. The Resource Identifier (RID) of a Dataset. The Resource Identifier (RID) of a Transaction. Response body. The Resource Identifier (RID) of a Transaction. The type of a Transaction. Enum values: APPEND, UPDATE, SNAPSHOT, DELETE. The status of a Transaction. Enum values: ABORTED, COMMITTED, OPEN. The timestamp when the transaction was created, in ISO 8601 timestamp format. The timestamp when the transaction was closed, in ISO 8601 timestamp format. Examples. Error responses.
