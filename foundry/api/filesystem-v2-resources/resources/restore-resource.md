---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/resources/restore-resource/"
title: "Restore Resource \u2022 API Reference"
---
# Restore Resource

## Endpoint

Restore the given resource and any directly trashed ancestors from the trash. If the resource is not
trashed, this operation will be ignored.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-write`.

**operationId:** v2.restoreResource

**path:** /api/v2/filesystem/resources/{resourceRid}/restore

### Operation Type

### Scopes

| name |
| --- |
| api:filesystem-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| resourceRid | stringType | True | The unique resource identifier (RID) of a Resource. |

### Error Responses

| name | description |
| --- | --- |
| ResourceNotDirectlyTrashed | The Resource is not directly trashed. |
| RestoreResourcePermissionDenied | Could not restore the Resource. |
| ResourceNotFound | The given Resource could not be found. |
