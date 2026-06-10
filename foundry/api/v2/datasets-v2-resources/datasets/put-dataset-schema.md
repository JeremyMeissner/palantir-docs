---
source_url: "https://www.palantir.com/docs/foundry/api/v2/datasets-v2-resources/datasets/put-dataset-schema/"
parquet_url: "/foundry/api/v2/datasets-v2-resources/datasets/put-dataset-schema/"
title: "Put Dataset Schema"
fetched_at: "2026-05-12T19:34:37.562Z"
---
Put Dataset Schema. Adds a schema on an existing dataset using a PUT request. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:datasets-write. Path parameters. The Resource Identifier (RID) of a Dataset. Request body. The name of a Branch. The dataframe reader used for reading the dataset schema. Defaults to PARQUET. Enum values: AVRO, CSV, PARQUET, DATASOURCE. The Resource Identifier (RID) of the end Transaction. The schema that will be added. Response body. The name of a Branch. The Resource Identifier (RID) of a Transaction. The schema for a Foundry dataset. Files uploaded to this dataset must match this schema. The version identifier of a dataset schema. Examples. Error responses.
