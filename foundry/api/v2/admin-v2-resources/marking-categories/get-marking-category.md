---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/marking-categories/get-marking-category/"
title: "Get Marking Category"
---
# Get Marking Category

Get the MarkingCategory with the specified id. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-read. Path parameters. The ID of a marking category. For user-created categories, this will be a UUID. Markings associated with Organizations are placed in a category with ID "Organization". Response body. The ID of a marking category. For user-created categories, this will be a UUID. Markings associated with Organizations are placed in a category with ID "Organization". Enum values: CONJUNCTIVE, DISJUNCTIVE. Enum values: MANDATORY, CBAC. The time at which the resource was created. The Foundry user who created this resource. Examples. Error responses.
