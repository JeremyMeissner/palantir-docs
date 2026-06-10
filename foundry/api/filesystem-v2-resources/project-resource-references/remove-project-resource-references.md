---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/project-resource-references/remove-project-resource-references/"
title: "Remove Project Resource References \u2022 API Reference"
---
# Remove Project Resource References

## Endpoint

Remove references from the given project

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-write`.

**operationId:** v2.removeProjectResourceReferences

**path:** /api/v2/filesystem/projects/{projectRid}/references/remove

### Operation Type

### Scopes

| name |
| --- |
| api:filesystem-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| projectRid | stringType | True | The unique resource identifier (RID) of a Project. |

### Request

#### Body

**name:** RemoveProjectResourceReferencesRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| resources | listType | False | The resource identifiers to remove as references. These may be either filesystem or external resource identifiers. |

**example:** {"resources":["ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da"]}

### Error Responses

| name | description |
| --- | --- |
| InvalidResourceReference | The resource reference is invalid. This can occur when the resource identifier is malformed, the resource type does not match the reference type, or the resource cannot be added as a reference. |
| InvalidProject | The provided resource identifier does not refer to a valid project. |
| RemoveProjectResourceReferencesPermissionDenied | Could not remove the ProjectResourceReference. |
| ProjectNotFound | The given Project could not be found. |
| ResourceNotFound | The given Resource could not be found. |
