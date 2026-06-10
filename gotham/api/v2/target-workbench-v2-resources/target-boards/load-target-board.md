---
source_url: "https://www.palantir.com/docs/gotham/api/v2/target-workbench-v2-resources/target-boards/load-target-board/"
title: "Load Target Board"
---
# Load Target Board

Load Target Board by RID. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:target-read. Path parameters. The unique identifier for a Target Board. Response body. Success response with the requested Target Board. The current version of the Target Board to be modified. The archive operation will be transformed against any concurrent operations made since this version. If there are any conflicting edits that result in changes to these operations when they're applied, that will be noted in the response. Examples. Error responses.
