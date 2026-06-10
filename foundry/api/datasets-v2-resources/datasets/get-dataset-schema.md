---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/datasets/get-dataset-schema/"
title: "Get Dataset Schema \u2022 API Reference"
---
# Get Dataset Schema

## Endpoint

Gets a dataset's schema. If no `endTransactionRid` is provided, the latest committed version will be used.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-read`.

**operationId:** v2.getDatasetSchema

**path:** /api/v2/datasets/{datasetRid}/getSchema

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of a Dataset. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branchName | stringType | False | The name of a Branch. |
| endTransactionRid | stringType | False | The Resource Identifier (RID) of the end Transaction. If a user does not provide a value, the RID of the latest committed transaction will be used. |
| versionId | stringType | False | The schema version that should be used. If none is provided, the latest version will be used. |

### Response

#### Body

**name:** GetDatasetSchemaResponse

**example:** {"endTransactionRid":"ri.foundry.main.transaction.0a0207cb-26b7-415b-bc80-66a3aa3933f4","schema":{"fieldSchemaList":[{"name":"id","type":"LONG","nullable":false,"customMetadata":{"description":"Primary key"}},{"name":"event_time","type":"TIMESTAMP","nullable":false},{"name":"price","type":"DECIMAL","precision":10,"scale":2,"nullable":true},{"name":"tags","type":"ARRAY","nullable":true,"arraySubtype":{"type":"STRING","nullable":false}},{"name":"metrics","type":"STRUCT","nullable":true,"subSchemas":[{"name":"temperature","type":"DOUBLE","nullable":true},{"name":"humidity","type":"DOUBLE","nullable":true}]}]},"versionId":"0000000d-2acf-537c-a228-3a9fe3cdc523","branchName":"master"}

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| branchName | stringType | True | The name of a Branch. |
| endTransactionRid | stringType | True | The Resource Identifier (RID) of a Transaction. |
| schema | objectType | True | The schema for a Foundry dataset. Files uploaded to this dataset must match this schema. |
| versionId | stringType | True | The version identifier of a dataset schema. |

**example:** {"endTransactionRid":"ri.foundry.main.transaction.0a0207cb-26b7-415b-bc80-66a3aa3933f4","schema":{"fieldSchemaList":[{"name":"id","type":"LONG","nullable":false,"customMetadata":{"description":"Primary key"}},{"name":"event_time","type":"TIMESTAMP","nullable":false},{"name":"price","type":"DECIMAL","precision":10,"scale":2,"nullable":true},{"name":"tags","type":"ARRAY","nullable":true,"arraySubtype":{"type":"STRING","nullable":false}},{"name":"metrics","type":"STRUCT","nullable":true,"subSchemas":[{"name":"temperature","type":"DOUBLE","nullable":true},{"name":"humidity","type":"DOUBLE","nullable":true}]}]},"versionId":"0000000d-2acf-537c-a228-3a9fe3cdc523","branchName":"master"}

### Error Responses

| name | description |
| --- | --- |
| BranchNotFound | The requested branch could not be found, or the client token does not have access to it. |
| DatasetNotFound | The requested dataset could not be found, or the client token does not have access to it. |
| SchemaNotFound | A schema could not be found for the given dataset and branch, or the client token does not have access to it. |
| InvalidParameterCombination | The given parameters are individually valid but cannot be used in the given combination. |
| DatasetViewNotFound | The requested dataset view could not be found. A dataset view represents the effective file contents of a dataset for a branch at a point in time, calculated from transactions (SNAPSHOT, APPEND, UPDATE, DELETE). The view may not exist if the dataset has no transactions, contains no files, the branch is not valid, or the client token does not have access to it. |
| GetDatasetSchemaPermissionDenied | Could not getSchema the Dataset. |
