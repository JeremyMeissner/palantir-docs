---
source_url: "https://www.palantir.com/docs/foundry/api/data-health-v2-resources/checks/delete-check/"
title: "Delete Check \u2022 API Reference"
---
# Delete Check

## Endpoint

:::callout{theme=warning title=Warning}
  This endpoint is in preview and may be modified or removed at any time.
  To use this endpoint, add `preview=true` to the request query parameters.
:::

Delete the Check with the specified rid.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:data-health-write`.

**operationId:** v2.deleteCheck

**path:** /api/v2/dataHealth/checks/{checkRid}

### Operation Type

### Scopes

| name |
| --- |
| api:data-health-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| checkRid | stringType | True | The unique resource identifier (RID) of a Data Health Check. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| preview | booleanType | False | Enables the use of preview functionality. |

### Error Responses

| name | description |
| --- | --- |
| DeleteCheckPermissionDenied | Could not delete the Check. |
| CheckNotFound | The given Check could not be found. |
