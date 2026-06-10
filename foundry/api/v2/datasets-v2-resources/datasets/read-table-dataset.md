---
source_url: "https://www.palantir.com/docs/foundry/api/v2/datasets-v2-resources/datasets/read-table-dataset/"
title: "Read Table Dataset"
---
# Read Table Dataset

Gets the content of a dataset as a table in the specified format. This endpoint currently does not support views (virtual datasets composed of other datasets). Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:datasets-read. Path parameters. The Resource Identifier (RID) of a Dataset. Query parameters. The name of the Branch. The Resource Identifier (RID) of the start Transaction. The Resource Identifier (RID) of the end Transaction. The export format. Must be ARROW or CSV. Enum values: ARROW, CSV. A subset of the dataset columns to include in the result. Defaults to all columns. A limit on the number of rows to return. Note that row ordering is non-deterministic. Response body. Examples. Error responses.
