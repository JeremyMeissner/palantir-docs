---
source_url: "https://www.palantir.com/docs/gotham/api/v2/target-workbench-v2-resources/target-boards/modify-target-board/"
title: "Modify Target Board"
---
# Modify Target Board

Modify a Target Board by RID. Sets the current state of a Collection. Any fields, except hptl, not supplied will result in removal if there was a value present. Trying to set hptl to empty when there's already a value will result in an INVALID_ARGUMENT exception. You cannot modify the hptl field if a value is already set. Fields that are not supported by the OpenAPI layer will remain unmodified. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:target-write. Path parameters. The unique identifier for a Target Board. Request body. Configuration for a target board. The current version of the Target Board to be modified. The archive operation will be transformed against any concurrent operations made since this version. If there are any conflicting edits that result in changes to these operations when they're applied, that will be noted in the response. Response body. An empty response object indicating the request was successful. Examples. Error responses.
