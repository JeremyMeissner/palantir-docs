---
source_url: "https://www.palantir.com/docs/foundry/api/v1/datasets-resources/branches/create-branch/"
title: "Create Branch"
---
# Create Branch

Creates a branch on an existing dataset. A branch may optionally point to a (committed) transaction. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:datasets-write. Path parameters. The Resource Identifier (RID) of the Dataset on which to create the Branch. Request body. The identifier (name) of a Branch. The Resource Identifier (RID) of a Transaction. Response body. A Branch of a Dataset. The identifier (name) of a Branch. The Resource Identifier (RID) of a Transaction. Examples. Error responses.
