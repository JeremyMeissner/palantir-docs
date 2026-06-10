---
source_url: "https://www.palantir.com/docs/foundry/api/filesystem-v2-resources/resources/get-resources-batch/"
title: "Get Resources Batch \u2022 API Reference"
---
# Get Resources Batch

## Endpoint

Fetches multiple resources in a single request.
Returns a map from RID to the corresponding resource. If a resource does not exist, or if it is a root folder or space, its RID will not be included in the map.
At most 1,000 resources should be requested at once.

The maximum batch size for this endpoint is 1000.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:filesystem-read`.

**operationId:** v2.getResourcesBatch

**path:** /api/v2/filesystem/resources/getBatch

### Operation Type

### Scopes

| name |
| --- |
| api:filesystem-read |

### Request

#### Body

**name:** body

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| GetResourcesBatchRequestElement | objectType | True |  |

**example:** [{"resourceRid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da"}]

### Response

#### Body

**name:** GetResourcesBatchResponse

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | mapType | False |  |
