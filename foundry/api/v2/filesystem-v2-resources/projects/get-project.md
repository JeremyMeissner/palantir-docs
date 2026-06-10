---
source_url: "https://www.palantir.com/docs/foundry/api/v2/filesystem-v2-resources/projects/get-project/"
title: "Get Project"
---
# Get Project

Get the Project with the specified rid. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:filesystem-read. Path parameters. The unique resource identifier (RID) of a Project. Response body. The unique resource identifier (RID) of a Project. The display name of the Project. Must be unique and cannot contain a / The description associated with the Project. The documentation associated with the Project. The full path to the resource, including the resource name itself. The Foundry user who created this resource. The Foundry user who last updated this resource. The time at which the resource was created. The time at which the resource was most recently updated. The trash status of the Project. Enum values: DIRECTLY_TRASHED, ANCESTOR_TRASHED, NOT_TRASHED. The Space Resource Identifier (RID) that the Project lives in. Whether role grants are allowed on individual resources within the Project. Examples. Error responses.
