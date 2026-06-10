---
source_url: "https://www.palantir.com/docs/foundry/api/v2/media-sets-v2-resources/media-sets/abort-media-transaction/"
title: "Abort Media Transaction"
---
# Abort Media Transaction

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Aborts an open transaction. Items uploaded to the media set during this transaction will be deleted. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:mediasets-write. Path parameters. The Resource Identifier (RID) of a Media Set in Foundry. An identifier which represents a transaction on a media set. Query parameters. A boolean flag that, when set to true, enables the use of beta features in preview mode. Examples.
