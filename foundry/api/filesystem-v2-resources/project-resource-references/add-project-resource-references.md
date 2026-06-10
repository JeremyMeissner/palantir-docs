---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/project-resource-references/add-project-resource-references/"
title: "Add Project Resource References \u2022 API Reference"
---
# Add Project Resource References

## Endpoint

Add references to the given project

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-write`.

**operationId:** v2.addProjectResourceReferences

**path:** /api/v2/filesystem/projects/{projectRid}/references/add

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

**name:** AddProjectResourceReferencesRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| resources | listType | False |  |

### Error Responses

| name | description |
| --- | --- |
| InvalidResourceReference | The resource reference is invalid. This can occur when the resource identifier is malformed, the resource type does not match the reference type, or the resource cannot be added as a reference. |
| InvalidProject | The provided resource identifier does not refer to a valid project. |
| AddProjectResourceReferencesPermissionDenied | Could not add the ProjectResourceReference. |
| ProjectNotFound | The given Project could not be found. |
| ResourceNotFound | The given Resource could not be found. |
