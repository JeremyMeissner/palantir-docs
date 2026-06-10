---
source_url: "https://www.palantir.com/docs/foundry/api/datasets-v2-resources/datasets/read-table-dataset/"
title: "Read Table Dataset \u2022 API Reference"
---
# Read Table Dataset

## Endpoint

Gets the content of a dataset as a table in the specified format.

This endpoint currently does not support views (virtual datasets composed of other datasets).

Third-party applications using this endpoint via OAuth2 must request the following operation scope: `api:datasets-read`.

**operationId:** v2.readTableDataset

**path:** /api/v2/datasets/{datasetRid}/readTable

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
| branchName | stringType | False | The name of the Branch. |
| startTransactionRid | stringType | False | The Resource Identifier (RID) of the start Transaction. |
| endTransactionRid | stringType | False | The Resource Identifier (RID) of the end Transaction. |
| format | enumType | True | The export format. Must be `ARROW` or `CSV`. |
| columns | listType | False | A subset of the dataset columns to include in the result. Defaults to all columns. |
| rowLimit | integerType | False | A limit on the number of rows to return. Note that row ordering is non-deterministic. |

### Response

#### Body

**name:** body

##### Format

### Error Responses

| name | description |
| --- | --- |
| ColumnTypesNotSupported | The dataset contains column types that are not supported. |
| ReadTableDatasetPermissionDenied | The provided token does not have permission to read the given dataset as a table. |
| ReadTableError | An error occurred while reading the table. Refer to the message for more details. |
| ReadTableRowLimitExceeded | The request to read the table generates a result that exceeds the allowed number of rows. For datasets not stored as Parquet there is a limit of 1 million rows. For datasets stored as Parquet there is no limit. |
| ReadTableTimeout | The request to read the table timed out. |
| DatasetReadNotSupported | The dataset does not support being read. |
| SchemaNotFound | A schema could not be found for the given dataset and branch, or the client token does not have access to it. |
| InvalidParameterCombination | The given parameters are individually valid but cannot be used in the given combination. |
