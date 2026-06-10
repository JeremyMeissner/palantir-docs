---
source_url: "https://www.palantir.com/docs/foundry/api/v1/datasets-resources/transactions/abort-transaction/"
parquet_url: "/foundry/api/v1/datasets-resources/transactions/abort-transaction/"
title: "Abort Transaction"
fetched_at: "2026-05-12T19:34:37.500Z"
---
Abort Transaction. Aborts an open Transaction. File modifications made on this Transaction are not preserved and the Branch is not updated. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:datasets-write. Path parameters. The Resource Identifier (RID) of the Dataset that contains the Transaction. The Resource Identifier (RID) of the Transaction. Response body. An operation that modifies the files within a dataset. The Resource Identifier (RID) of a Transaction. The type of a Transaction. Enum values: APPEND, UPDATE, SNAPSHOT, DELETE. The status of a Transaction. Enum values: ABORTED, COMMITTED, OPEN. The timestamp when the transaction was created, in ISO 8601 timestamp format. The timestamp when the transaction was closed, in ISO 8601 timestamp format. Examples. Error responses.
