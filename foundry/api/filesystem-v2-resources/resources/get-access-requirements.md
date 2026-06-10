---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/resources/get-access-requirements/"
title: "Get Access Requirements \u2022 API Reference"
---
# Get Access Requirements

## Endpoint

Returns a list of access requirements a user needs in order to view a resource. Access requirements are
composed of Organizations and Markings, and can either be applied directly to the resource or inherited.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-read`.

**operationId:** v2.getAccessRequirements

**path:** /api/v2/filesystem/resources/{resourceRid}/getAccessRequirements

### Operation Type

### Scopes

| name |
| --- |
| api:filesystem-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| resourceRid | stringType | True | The unique resource identifier (RID) of a Resource. |

### Response

#### Body

Access requirements for a resource are composed of Markings and Organizations. Organizations are disjunctive, 
while Markings are conjunctive.

**name:** AccessRequirements

**example:** {"markings":[{"markingId":"18212f9a-0e63-4b79-96a0-aae04df23336"}],"organizations":[{"organizationRid":"ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa","markingId":"18212f9a-0e63-4b79-96a0-aae04df23336"}]}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| organizations | listType | False |  |
| markings | listType | False |  |

**example:** {"markings":[{"markingId":"18212f9a-0e63-4b79-96a0-aae04df23336"}],"organizations":[{"organizationRid":"ri.multipass..organization.c30ee6ad-b5e4-4afe-a74f-fe4a289f2faa","markingId":"18212f9a-0e63-4b79-96a0-aae04df23336"}]}

### Error Responses

| name | description |
| --- | --- |
| GetAccessRequirementsPermissionDenied | Could not getAccessRequirements the Resource. |
| ResourceNotFound | The given Resource could not be found. |
