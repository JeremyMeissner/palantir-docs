---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/resources/remove-markings/"
title: "Remove Markings \u2022 API Reference"
---
# Remove Markings

## Endpoint

Removes Markings from a resource.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-write`.

**operationId:** v2.removeMarkings

**path:** /api/v2/filesystem/resources/{resourceRid}/removeMarkings

### Operation Type

### Scopes

| name |
| --- |
| api:filesystem-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| resourceRid | stringType | True | The unique resource identifier (RID) of a Resource. |

### Request

#### Body

**name:** RemoveMarkingsRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| markingIds | listType | False |  |

**example:** {"markingIds":["18212f9a-0e63-4b79-96a0-aae04df23336"]}

### Error Responses

| name | description |
| --- | --- |
| OrganizationMarkingNotSupported | Adding an organization marking as a regular marking is not supported. Use the organization endpoints on a  project resource instead. |
| ForbiddenOperationOnHiddenResource | Performing this operation on a hidden resource is not supported. |
| ForbiddenOperationOnAutosavedResource | Performing this operation on an autosaved resource is not supported. |
| MarkingNotFound | A provided marking ID cannot be found. |
| RemoveMarkingsPermissionDenied | Could not removeMarkings the Resource. |
| ResourceNotFound | The given Resource could not be found. |
