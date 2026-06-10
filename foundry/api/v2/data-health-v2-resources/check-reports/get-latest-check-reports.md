---
source_url: "https://www.palantir.com/docs/foundry/api/v2/data-health-v2-resources/check-reports/get-latest-check-reports/"
title: "Get Latest Check Reports"
---
# Get Latest Check Reports

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Get the most recent check reports for this Check. Reports are returned in reverse chronological order (most recent first). Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:data-health-read. Path parameters. The unique resource identifier (RID) of a Data Health Check. Query parameters. The maximum number of check reports to return. Defaults to 10. Maximum allowed value is 100. Enables the use of preview functionality. Response body. The response for getting the latest check reports. The list of check reports. Examples. Error responses.
