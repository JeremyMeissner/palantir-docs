---
source_url: "https://www.palantir.com/docs/foundry/api/v2/media-sets-v2-resources/media-sets/create-media-transaction/"
parquet_url: "/foundry/api/v2/media-sets-v2-resources/media-sets/create-media-transaction/"
title: "Create Media Transaction"
fetched_at: "2026-05-12T19:34:37.759Z"
---
Create Media Transaction. Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Creates a new transaction. Items uploaded to the media set while this transaction is open will not be reflected until the transaction is committed. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:mediasets-write. Path parameters. The Resource Identifier (RID) of a Media Set in Foundry. Query parameters. The branch on which to open the transaction. Defaults to master for most enrollments. A boolean flag that, when set to true, enables the use of beta features in preview mode. Response body. An identifier which represents a transaction on a media set. Examples.
