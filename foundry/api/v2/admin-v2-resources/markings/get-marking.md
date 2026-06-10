---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/markings/get-marking/"
title: "Get Marking"
---
# Get Marking

Get the Marking with the specified id. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-read. Path parameters. The ID of a security marking. Response body. The ID of a security marking. The ID of a marking category. For user-created categories, this will be a UUID. Markings associated with Organizations are placed in a category with ID "Organization". If this marking is associated with an Organization, its RID will be populated here. The time at which the resource was created. The Foundry user who created this resource. Examples. Error responses.
