---
source_url: "https://www.palantir.com/docs/foundry/api/v2/connectivity-v2-resources/file-imports/execute-file-import/"
parquet_url: "/foundry/api/v2/connectivity-v2-resources/file-imports/execute-file-import/"
title: "Execute File Import"
fetched_at: "2026-05-12T19:34:37.684Z"
---
Execute File Import. Executes the FileImport, which runs asynchronously as a Foundry Build. The returned BuildRid can be used to check the status via the Orchestration API. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:connectivity-file-import-execute. Path parameters. The Resource Identifier (RID) of a Connection (also known as a source). The Resource Identifier (RID) of a FileImport (also known as a batch sync). Response body. The RID of a Build. Examples. Error responses.
