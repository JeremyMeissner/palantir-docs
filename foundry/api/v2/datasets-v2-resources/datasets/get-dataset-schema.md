---
source_url: "https://www.palantir.com/docs/foundry/api/v2/datasets-v2-resources/datasets/get-dataset-schema/"
parquet_url: "/foundry/api/v2/datasets-v2-resources/datasets/get-dataset-schema/"
title: "Get Dataset Schema"
fetched_at: "2026-05-12T19:34:37.557Z"
---
Get Dataset Schema. Gets a dataset's schema. If no endTransactionRid is provided, the latest committed version will be used. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:datasets-read. Path parameters. The Resource Identifier (RID) of a Dataset. Query parameters. The name of a Branch. The Resource Identifier (RID) of the end Transaction. If a user does not provide a value, the RID of the latest committed transaction will be used. The schema version that should be used. If none is provided, the latest version will be used. Response body. The name of a Branch. The Resource Identifier (RID) of a Transaction. The schema for a Foundry dataset. Files uploaded to this dataset must match this schema. The version identifier of a dataset schema. Examples. Error responses.
