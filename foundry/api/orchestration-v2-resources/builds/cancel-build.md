---
source_url: "https://www.palantir.com/docs/foundry/api/orchestration-v2-resources/builds/cancel-build/"
title: "Cancel Build \u2022 API Reference"
---
# Cancel Build

## Endpoint

Request a cancellation for all unfinished jobs in a build. The build's status will not update immediately. This endpoint is asynchronous and a success response indicates that the cancellation request has been acknowledged and the build is expected to be canceled soon. If the build has already finished or finishes shortly after the request and before the cancellation, the build will not change.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:orchestration-write`.

**operationId:** v2.cancelBuild

**path:** /api/v2/orchestration/builds/{buildRid}/cancel

### Operation Type

### Scopes

| name |
| --- |
| api:orchestration-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| buildRid | stringType | True | The RID of a Build. |

### Error Responses

| name | description |
| --- | --- |
| CancelBuildPermissionDenied | Could not cancel the Build. |
