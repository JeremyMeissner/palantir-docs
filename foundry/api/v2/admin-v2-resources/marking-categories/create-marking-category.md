---
source_url: "https://www.palantir.com/docs/foundry/api/v2/admin-v2-resources/marking-categories/create-marking-category/"
title: "Create Marking Category"
---
# Create Marking Category

Warning. This endpoint is in preview and may be modified or removed at any time. To use this endpoint, add preview=true to the request query parameters. Creates a new MarkingCategory. Third-party applications using this endpoint via OAuth2 must request the following operation scope: api:admin-write. Query parameters. Enables the use of preview functionality. Request body. The initial permissions for the Marking Category. This can be changed later through MarkingCategoryPermission operations. The provided permissions must include at least one ADMINISTER role assignment. WARNING: If you do not list your own principal ID or the ID of a Group that you are a member of as an ADMINISTER, you will create a Marking Category that you cannot administer. Response body. The created MarkingCategory. The ID of a marking category. For user-created categories, this will be a UUID. Markings associated with Organizations are placed in a category with ID "Organization". Enum values: CONJUNCTIVE, DISJUNCTIVE. Enum values: MANDATORY, CBAC. The time at which the resource was created. The Foundry user who created this resource. Examples. Error responses.
