---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/datasets/put-dataset-schema/"
title: "Put Dataset Schema \u2022 API Reference"
---
# Put Dataset Schema

## Endpoint

Adds a schema on an existing dataset using a PUT request.

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-write`.

**operationId:** v2.putDatasetSchema

**path:** /api/v2/datasets/{datasetRid}/putSchema

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-write |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The Resource Identifier (RID) of a Dataset. |

### Request

#### Body

**name:** PutDatasetSchemaRequest

##### Children

| name | type | required | description |
| --- | --- | --- | --- |
| branchName | stringType | False | The name of a Branch. |
| dataframeReader | enumType | False | The dataframe reader used for reading the dataset schema. Defaults to PARQUET. |
| endTransactionRid | stringType | False | The Resource Identifier (RID) of the end Transaction. |
| schema | objectType | True | The schema that will be added. |

**example:** {"endTransactionRid":"ri.foundry.main.transaction.0a0207cb-26b7-415b-bc80-66a3aa3933f4","schema":{"fieldSchemaList":[{"name":"id","type":"LONG","nullable":false,"customMetadata":{"description":"Primary key"}},{"name":"event_time","type":"TIMESTAMP","nullable":false},{"name":"price","type":"DECIMAL","precision":10,"scale":2,"nullable":true},{"name":"tags","type":"ARRAY","nullable":true,"arraySubtype":{"type":"STRING","nullable":false}},{"name":"metrics","type":"STRUCT","nullable":true,"subSchemas":[{"name":"temperature","type":"DOUBLE","nullable":true},{"name":"humidity","type":"DOUBLE","nullable":true}]}]},"dataframeReader":"PARQUET","branchName":"master"}

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
| InvalidSchema | The schema failed validations |
| DatasetViewNotFound | The requested dataset view could not be found. A dataset view represents the effective file contents of a dataset for a branch at a point in time, calculated from transactions (SNAPSHOT, APPEND, UPDATE, DELETE). The view may not exist if the dataset has no transactions, contains no files, the branch is not valid, or the client token does not have access to it. |
| PutDatasetSchemaPermissionDenied | Could not putSchema the Dataset. |
