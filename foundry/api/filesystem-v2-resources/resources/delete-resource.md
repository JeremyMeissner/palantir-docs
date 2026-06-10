---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/resources/delete-resource/"
title: "Delete Resource \u2022 API Reference"
---
# Delete Resource

## Endpoint

Move the given resource to the trash. Following this operation, the resource can be restored, using the
`restore` operation, or permanently deleted using the `permanentlyDelete` operation.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-write`.

**operationId:** v2.deleteResource

**path:** /api/v2/filesystem/resources/{resourceRid}

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
| TrashingSpaceNotSupported | Spaces cannot be trashed. |
| TrashingAutosavedResourcesNotSupported | Auto-saved Resources cannot be trashed. |
| TrashingHiddenResourcesNotSupported | Hidden Resources cannot be trashed. |
| DeleteResourcePermissionDenied | Could not delete the Resource. |
| ResourceNotFound | The given Resource could not be found. |
