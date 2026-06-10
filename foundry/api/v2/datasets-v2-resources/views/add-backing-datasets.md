---
source_url: "https://www.palantir.com/docs/foundry/api/v2/datasets-v2-resources/views/add-backing-datasets/"
title: "Add Backing Datasets"
---
# Add Backing Datasets

Adds one or more backing datasets to a View. Any duplicates with the same dataset RID and branch name are ignored. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:datasets-write. Path parameters. The rid of the View. Request body. The name of a Branch. Response body. The rid of the View. The unique resource identifier (RID) of a Folder. The branch name of the View. If not specified, defaults to master for most enrollments. The primary key of the dataset. Primary keys are treated as guarantees provided by the creator of the dataset. Examples. Error responses.
