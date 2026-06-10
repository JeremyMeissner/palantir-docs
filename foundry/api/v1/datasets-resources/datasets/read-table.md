---
source_url: "https://www.palantir.com/docs/foundry/api/v1/datasets-resources/datasets/read-table/"
parquet_url: "/foundry/api/v1/datasets-resources/datasets/read-table/"
title: "Read Table"
fetched_at: "2026-05-12T19:34:37.504Z"
---
Read Table. Gets the content of a dataset as a table in the specified format. This endpoint currently does not support views (virtual datasets composed of other datasets). For more information, refer to the views documentation. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:datasets-read. Path parameters. The RID of the Dataset. Query parameters. The identifier (name) of the Branch. The Resource Identifier (RID) of the start Transaction. The Resource Identifier (RID) of the end Transaction. The export format. Must be ARROW or CSV. Enum values: ARROW, CSV. A subset of the dataset columns to include in the result. Defaults to all columns. A limit on the number of rows to return. Note that row ordering is non-deterministic. Response body. The content stream. Examples. Error responses.
