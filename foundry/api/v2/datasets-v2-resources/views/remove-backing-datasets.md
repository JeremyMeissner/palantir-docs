---
source_url: "https://www.palantir.com/docs/foundry/api/v2/datasets-v2-resources/views/remove-backing-datasets/"
title: "Remove Backing Datasets"
---
# Remove Backing Datasets

Removes specified backing datasets from a View. Removing a dataset triggers a SNAPSHOT transaction on the next update. If a specified dataset does not exist, no error is thrown. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:datasets-write. Path parameters. The rid of the View. Request body. The name of a Branch. Response body. The rid of the View. The unique resource identifier (RID) of a Folder. The branch name of the View. If not specified, defaults to master for most enrollments. The primary key of the dataset. Primary keys are treated as guarantees provided by the creator of the dataset. Examples. Error responses.
