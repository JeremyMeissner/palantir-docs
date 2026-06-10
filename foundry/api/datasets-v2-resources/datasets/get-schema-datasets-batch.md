---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/datasets/get-schema-datasets-batch/"
title: "Get Schema Datasets Batch \u2022 API Reference"
---
# Get Schema Datasets Batch

## Endpoint

Fetch schemas for multiple datasets in a single request. Datasets not found 
or inaccessible to the user will be omitted from the response.

The maximum batch size for this endpoint is 1000.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-read`.

**operationId:** v2.getSchemaDatasetsBatch

**path:** /api/v2/datasets/getSchemaBatch

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-read |

### Request

#### Body

**name:** body

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| GetSchemaDatasetsBatchRequestElement | objectType | True |  |

**example:** [{"endTransactionRid":"ri.foundry.main.transaction.0a0207cb-26b7-415b-bc80-66a3aa3933f4","datasetRid":"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da","versionId":"0000000d-2acf-537c-a228-3a9fe3cdc523","branchName":"master"}]

### Response

#### Body

**name:** GetSchemaDatasetsBatchResponse

**example:** {"data":{"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da":{"endTransactionRid":"ri.foundry.main.transaction.0a0207cb-26b7-415b-bc80-66a3aa3933f4","schema":{"fieldSchemaList":[{"name":"id","type":"LONG","nullable":false,"customMetadata":{"description":"Primary key"}},{"name":"event_time","type":"TIMESTAMP","nullable":false},{"name":"price","type":"DECIMAL","precision":10,"scale":2,"nullable":true},{"name":"tags","type":"ARRAY","nullable":true,"arraySubtype":{"type":"STRING","nullable":false}},{"name":"metrics","type":"STRUCT","nullable":true,"subSchemas":[{"name":"temperature","type":"DOUBLE","nullable":true},{"name":"humidity","type":"DOUBLE","nullable":true}]}]},"versionId":"0000000d-2acf-537c-a228-3a9fe3cdc523","branchName":"master"}}}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| data | mapType | False |  |

**example:** {"data":{"ri.foundry.main.dataset.c26f11c8-cdb3-4f44-9f5d-9816ea1c82da":{"endTransactionRid":"ri.foundry.main.transaction.0a0207cb-26b7-415b-bc80-66a3aa3933f4","schema":{"fieldSchemaList":[{"name":"id","type":"LONG","nullable":false,"customMetadata":{"description":"Primary key"}},{"name":"event_time","type":"TIMESTAMP","nullable":false},{"name":"price","type":"DECIMAL","precision":10,"scale":2,"nullable":true},{"name":"tags","type":"ARRAY","nullable":true,"arraySubtype":{"type":"STRING","nullable":false}},{"name":"metrics","type":"STRUCT","nullable":true,"subSchemas":[{"name":"temperature","type":"DOUBLE","nullable":true},{"name":"humidity","type":"DOUBLE","nullable":true}]}]},"versionId":"0000000d-2acf-537c-a228-3a9fe3cdc523","branchName":"master"}}}
