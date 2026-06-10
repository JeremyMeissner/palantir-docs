---
source_url: "https://www.palantir.com/docs/foundry/api/v2/datasets-v2-resources/branches/create-branch/"
parquet_url: "/foundry/api/v2/datasets-v2-resources/branches/create-branch/"
title: "Create Branch"
fetched_at: "2026-05-12T19:34:37.546Z"
---
Create Branch. Creates a branch on an existing dataset. A branch may optionally point to a (committed) transaction. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:datasets-write. Path parameters. The Resource Identifier (RID) of a Dataset. Request body. The most recent OPEN or COMMITTED transaction on the branch. This will never be an ABORTED transaction. The name of a Branch. Response body. The created Branch. The name of a Branch. The most recent OPEN or COMMITTED transaction on the branch. This will never be an ABORTED transaction. Examples. Error responses.
