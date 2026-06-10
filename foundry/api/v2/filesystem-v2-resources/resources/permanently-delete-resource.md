---
source_url: "https://www.palantir.com/docs/foundry/api/v2/filesystem-v2-resources/resources/permanently-delete-resource/"
title: "Permanently Delete Resource"
---
# Permanently Delete Resource

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Permanently delete the given resource from the trash. If the Resource is not directly trashed, a ResourceNotTrashed error will be thrown. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:filesystem-write. Path parameters. The unique resource identifier (RID) of a Resource. Query parameters. Enables the use of preview functionality. Examples. Error responses.
