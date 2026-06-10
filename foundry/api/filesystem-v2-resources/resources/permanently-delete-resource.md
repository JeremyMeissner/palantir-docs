---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/resources/permanently-delete-resource/"
title: "Permanently Delete Resource \u2022 API Reference"
---
# Permanently Delete Resource

## Endpoint

Permanently delete the given resource from the trash. If the Resource is not directly trashed, a
`ResourceNotTrashed` error will be thrown.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-write`.

**operationId:** v2.permanentlyDeleteResource

**path:** /api/v2/filesystem/resources/{resourceRid}/permanentlyDelete

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
| ResourceNotTrashed | The Resource should be directly trashed before being permanently deleted. |
| PermanentlyDeleteResourcePermissionDenied | Could not permanentlyDelete the Resource. |
| ResourceNotFound | The given Resource could not be found. |
