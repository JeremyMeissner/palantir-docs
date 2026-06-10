---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-resources/datasets/read-table/"
title: "Read Table \u2022 API Reference"
---
# Read Table

## Endpoint

Gets the content of a dataset as a table in the specified format.

This endpoint currently does not support views (virtual datasets composed of other datasets). For more information, refer to the [views documentation](/docs/foundry/data-integration/views).

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-read`.

**operationId:** v1.readTable

**path:** /api/v1/datasets/{datasetRid}/readTable

### Operation Type

### Scopes

| name |
| --- |
| api:datasets-read |

### Path Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| datasetRid | stringType | True | The RID of the Dataset. |

### Query Parameters

| name | type | required | description |
| --- | --- | --- | --- |
| branchId | stringType | False | The identifier (name) of the Branch. |
| startTransactionRid | stringType | False | The Resource Identifier (RID) of the start Transaction. |
| endTransactionRid | stringType | False | The Resource Identifier (RID) of the end Transaction. |
| format | enumType | True | The export format. Must be `ARROW` or `CSV`. |
| columns | listType | False | A subset of the dataset columns to include in the result. Defaults to all columns. |
| rowLimit | integerType | False | A limit on the number of rows to return. Note that row ordering is non-deterministic. |

### Response

#### Body

The content stream.

**name:** body

##### Format

### Error Responses

| name | description |
| --- | --- |
| InvalidParameterCombination | The given parameters are individually valid but cannot be used in the given combination. |
| SchemaNotFound | A schema could not be found for the given dataset and branch, or the client token does not have access to it. |
| ReadTablePermissionDenied | The provided token does not have permission to read the given dataset as a table. |
| ColumnTypesNotSupported | The dataset contains column types that are not supported. |
| DatasetReadNotSupported | The dataset does not support being read. |
