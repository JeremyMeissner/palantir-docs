---
source_url: "https://www.palantir.com/docs/foundry/api/v2/connectivity-v2-resources/table-imports/execute-table-import/"
parquet_url: "/foundry/api/v2/connectivity-v2-resources/table-imports/execute-table-import/"
title: "Execute Table Import"
fetched_at: "2026-05-12T19:34:37.688Z"
---
Execute Table Import. Executes the TableImport, which runs asynchronously as a Foundry Build. The returned BuildRid can be used to check the status via the Orchestration API. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:connectivity-table-import-execute. Path parameters. The Resource Identifier (RID) of a Connection (also known as a source). The Resource Identifier (RID) of a TableImport (also known as a batch sync). Response body. The RID of a Build. Examples. Error responses.
