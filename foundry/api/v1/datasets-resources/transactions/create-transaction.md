---
source_url: "https://www.palantir.com/docs/foundry/api/v1/datasets-resources/transactions/create-transaction/"
parquet_url: "/foundry/api/v1/datasets-resources/transactions/create-transaction/"
title: "Create Transaction"
fetched_at: "2026-05-12T19:34:37.502Z"
---
Create Transaction. Creates a Transaction on a Branch of a Dataset. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:datasets-write. Path parameters. The Resource Identifier (RID) of the Dataset on which to create the Transaction. Query parameters. The identifier (name) of the Branch on which to create the Transaction. Defaults to master for most enrollments. Request body. The type of a Transaction. Enum values: APPEND, UPDATE, SNAPSHOT, DELETE. Response body. An operation that modifies the files within a dataset. The Resource Identifier (RID) of a Transaction. The type of a Transaction. Enum values: APPEND, UPDATE, SNAPSHOT, DELETE. The status of a Transaction. Enum values: ABORTED, COMMITTED, OPEN. The timestamp when the transaction was created, in ISO 8601 timestamp format. The timestamp when the transaction was closed, in ISO 8601 timestamp format. Examples. Error responses.
